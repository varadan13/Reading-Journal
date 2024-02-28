

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

