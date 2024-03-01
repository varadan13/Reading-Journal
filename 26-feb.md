

# Reading-Journal

## Week of 26 Feb

>>

1. [x] [https://www.yieldcode.blog/post/how-to-stay-junior-forever/](https://www.yieldcode.blog/post/how-to-stay-junior-forever/)

>> One last advice–abolish the copy-paste. So many developers, whom I mentored, simply copy-paste everything. Code snippets, function declarations, etc. I know how to initialize a git repository, because I do it by hand every time. Most people simply copy the instructions from GitHub or Google. And if you are scared about being unproductive–remember that you are not judged by how much code you write, or how fast you complete the assignment.

>> If you want to stay junior forever, keep using AI and other code assisting tools.
>>

------

2. [x] [https://surfingcomplexity.blog/2024/02/17/what-if-everybody-did-everything-right/](https://surfingcomplexity.blog/2024/02/17/what-if-everybody-did-everything-right/)

## What if everybody did everything right?

>> Instead of asking these questions What did we do wrong here? What didn’t we do that we should have? ask What information did people know in the moment? What were the constraints that people were operating under? or how did this incident happen, assuming that everybody did everything right?
>>
>> 

-------
3. [x] [https://zerodha.tech/blog/1-5-million-pdfs-in-25-minutes/](https://zerodha.tech/blog/1-5-million-pdfs-in-25-minutes/)

## 1.5+ million PDFs in 25 minutes
```txt
1. A Python application reads various end-of-the-day CSV dumps coming from exchanges to generate HTML using a **Jinja template.**
2. Chrome, via **Puppeteer**, converts this HTML into PDF format.
3. A Java-based command-line interface (CLI) tool is then used to digitally sign the PDFs.
4. **Self hosted Postal SMTP servers** to send signed PDFs over email.

process took between 7 to 8 hours to complete
```

```txt
Data processing -> PDF generation -> PDF signing -> e-mailing PDFs
```

![new architecture](https://zerodha.tech/static/images/cnotes_wf_1.png)

```txt
The first sequence in our chained jobs workflow begins with a generator worker processing various CSV files to create templates for PDF files. This is then pushed into the queue as a job for the next worker, say the PDF generator, to pick up. Various different kinds of workers upon picking up their designated jobs, retrieve the relevant file from S3, process it, and then upload the output back to S3. So, for a user’s contract note PDF to be delivered to them via e-mail, their data passes through four workers (process data -> generate PDF -> sign PDF -> e-mail PDF), where each worker after doing its job, dumps the resultant file to S3 for the next worker to pick up.

The global job states are stored in a Redis instance. It serves a dual role in this architecture: as a backend broker facilitating the distribution of jobs among workers and as a storage medium for the status of each job. By querying Redis, we can track the number of jobs processed or identify any failures. For jobs that fail, targeted retries are initiated for users whose jobs previously failed or were not processed.
```

```txt
 Typst is used for pdf generation
```

```txt
OpenPDF to contract
``` 

-------

4. [x] [https://brooker.co.za/blog/2024/02/06/time.html](https://brooker.co.za/blog/2024/02/06/time.html)

## How Do You Spend Your Time?

```txt
IC (individual contributor) work This includes writing code, reading code, reviewing code, debugging, testing, standing around a whiteboard talking code and design, writing design docs, reviewing design docs, and so on. The core stuff that is the practice of software engineering.
Mentoring and Teaching This includes ad-hoc mentoring, standing one-on-ones2, and simply having time open on my calendar for the “do you have a few minutes to chat about my career?” conversations with folks near me. I also tend to put things like tech talks into this bucket.
Strategic Stuff What are we doing next year? What do the next five years look like? Where are the industry trends going? What are the new things our customers are thinking about that seems like it could be big? What skills am I going to need? What skills are the folks in my organization going to need?
Rhythm of Business This is the day-to-day. The way it looks has varied a lot over my career (more business reviews, less sprint planning), but includes everything involved in getting hands-on with the business. This includes the technical side (operations reviews, security meetings, looking into tickets and metrics, that kind of thing), money side (business reviews, etc), and people side (talent reviews, interviewing, and so on).
Learning I put aside time during my work day to learn things, including reading papers, implementing algorithms I think are potentially important, reading books, and similar activities. This often feels hard to justify, but isn’t - over time I’ve gathered a good set of success stories of business value of me spending my time this way3.
Customers I like talking to customers, and some of them like talking to me. Customers are the most important thing to stay connected to.
```

5. [x] [https://tkdodo.eu/blog/avoiding-hydration-mismatches-with-use-sync-external-store?ck_subscriber_id=1921253367](https://tkdodo.eu/blog/avoiding-hydration-mismatches-with-use-sync-external-store?ck_subscriber_id=1921253367)

### Avoiding Hydration Mismatches with useSyncExternalStore

```jsx
    <span suppressHydrationWarning>
      Last updated at: {date.toLocaleDateString()}
    </span>
```

```jsx
const useIsClient = () => {
  const [isClient, setIsClient] = React.useState(false);

  React.useEffect(() => {
    setIsClient(true);
  }, []);

  return isClient;
};

const Component = () => {
  const isClient = useIsClient();
  if (!isClient) {
    return null;
  }
  return <InnerComponent />;
};
```
Improved useIsClient
```jsx
const useIsClient = () => {
  const [isClient, setIsClient] = React.useState(!!window);

  React.useEffect(() => {
    if (!isClient){
    setIsClient(true);
   }
  }, []);

  return isClient;
};

const Component = () => {
  const isClient = useIsClient();
  if (!isClient) {
    return null;
  }
  return <InnerComponent />;
};
```

```jsx
function ClientGate({ children }) {
  const isServer = React.useSyncExternalStore(
    emptySubscribe,
    () => false,
    () => true
  )

  return isServer ? null : children()
}

function App() {
  return (
    <main>
      Hello Server
      <ClientGate>{() => `Hello Client ${window.title}`}</ClientGate>
    </main>
  )
}
```

----------

6. [x] [https://shubhamjain.co/2024/02/29/why-is-number-package-have-59m-downloads/](https://shubhamjain.co/2024/02/29/why-is-number-package-have-59m-downloads/)

## Why Does 'is-number' Package Have 59M Weekly Downloads?

```txt
tailwindcss -> chokidar -> braces -> fill-range -> to-regex-range -> is-number
```

```txt
npm should differentiate between direct and indirect downloads. I am not certain if it’s possible with how npm works, but downloads triggered by a dependency don’t accurately reflect the popularity of the package. People who visit the npm page are usually unaware of how the numbers work.

There should be a concentrated effort to replace the packages causing this mess with packages that inline their dependencies.

Like Bundlephobia, there should be a website that lists the total number of packages you’ll end up downloading when you include the dependency. Hopefully, it will encourage the community to seek packages with fewer indirect dependencies.
```
----

# Code snippet involving Promise.race and abortSignal;

```ts
export const m4aDuration = async (path: string): Promise<number> => {
  const controller = new AbortController();
  const duration = await Promise.race([
    search(path, controller.signal),
    search(path, controller.signal, true)
  ]);
  controller.abort();
  return duration;
};
```

This TypeScript code defines an asynchronous function `m4aDuration` that calculates the duration of an audio file in the M4A format. Let's break it down:

1. **AbortController Initialization:**
   ```typescript
   const controller = new AbortController();
   ```
   An `AbortController` is created. This controller allows you to abort an asynchronous operation if needed.

2. **Promise.race:**
   ```typescript
   const duration = await Promise.race([
     search(path, controller.signal),
     search(path, controller.signal, true)
   ]);
   ```
   The `Promise.race` function is used to race between two promises. The promises are created by calling the `search` function with different parameters.

   - `search(path, controller.signal)`: This is the first promise. It seems like a search operation for the given `path` using the `controller.signal` as an abort signal.
   - `search(path, controller.signal, true)`: This is the second promise. It also involves a search operation with the same `path` and `controller.signal`, but with an additional boolean parameter set to `true`.

   The `Promise.race` will resolve with the value of the first promise (either the result of the first search or the result of the second search, whichever finishes first).

3. **Abort and Return:**
   ```typescript
   controller.abort();
   return duration;
   ```
   The `controller.abort()` is called to abort any ongoing operations. This is important because the `Promise.race` only resolves with the value of the first completed promise, and the other ongoing promise should be aborted to avoid unnecessary computations.

   Finally, the function returns the `duration` obtained from the resolved promise.

Without the implementation of the `search` function, it's not possible to provide a complete understanding of what this code is doing. The `search` function likely involves some asynchronous operation related to determining the duration of the M4A audio file.

----
