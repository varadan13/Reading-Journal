# Reading-Journal

## Week of 19 Feb

>>

1. [https://heydonworks.com/article/offloading-javascript-with-custom-properties/](https://heydonworks.com/article/offloading-javascript-with-custom-properties/)

2. [https://www.phpied.com/bytes-normal-web-font-study-google-fonts/](https://www.phpied.com/bytes-normal-web-font-study-google-fonts/)

3. [https://searchengineland.com/nlp-seo-techniques-tools-strategies-437392](https://searchengineland.com/nlp-seo-techniques-tools-strategies-437392)

4. [https://www.seroundtable.com/google-rankings-disavowing-toxic-links-36881.html](https://www.seroundtable.com/google-rankings-disavowing-toxic-links-36881.html)

5. [https://www.searchenginejournal.com/google-updates-relcanonical-documentation/508430/](https://www.searchenginejournal.com/google-updates-relcanonical-documentation/508430/)

6. [https://moz.com/blog/addictive-content](https://moz.com/blog/addictive-content)

7. [https://www.wix.com/seo/learn/resource/ecommerce-link-building-strategies](https://www.wix.com/seo/learn/resource/ecommerce-link-building-strategies)

8. [https://learningseo.io/seo_roadmap/deepen-knowledge/content/content-pruning/](https://learningseo.io/seo_roadmap/deepen-knowledge/content/content-pruning/)

9. [https://ntietz.com/blog/great-management-and-leadership-books-for-the-technical-track/](https://ntietz.com/blog/great-management-and-leadership-books-for-the-technical-track/)

10. [https://www.sonarsource.com/learn/devops-transformation-static-code-analysis/?utm_medium%20=paid&utm_source=pointer&utm_campaign=ss-devops-transformation&utm_content=blast-use%20-case-240220-x&utm_term=ww-psp-x](https://www.sonarsource.com/learn/devops-transformation-static-code-analysis/?utm_medium%20=paid&utm_source=pointer&utm_campaign=ss-devops-transformation&utm_content=blast-use%20-case-240220-x&utm_term=ww-psp-x)

11. [https://www.edbatista.com/2024/02/jennifer-ouyang-altman-on-empty-questions.html](https://www.edbatista.com/2024/02/jennifer-ouyang-altman-on-empty-questions.html)

12. [https://avc.com/2012/02/the-management-team-guest-post-from-joel-spolsky/](https://avc.com/2012/02/the-management-team-guest-post-from-joel-spolsky/)

13. [https://adam.nels.onl/blog/maybe-everything-is-a-coroutine/](https://adam.nels.onl/blog/maybe-everything-is-a-coroutine/)

14. [https://arindam1729.hashnode.dev/private-routes-in-react?utm_source=newsletter.reactdigest.net&utm_medium=newsletter&utm_campaign=how-to-center-a-div](https://arindam1729.hashnode.dev/private-routes-in-react?utm_source=newsletter.reactdigest.net&utm_medium=newsletter&utm_campaign=how-to-center-a-div)

15. [https://www.freecodecamp.org/news/improve-reactjs-code/?utm_source=newsletter.reactdigest.net&utm_medium=newsletter&utm_campaign=how-to-center-a-div](https://www.freecodecamp.org/news/improve-reactjs-code/?utm_source=newsletter.reactdigest.net&utm_medium=newsletter&utm_campaign=how-to-center-a-div)

16. [x] ## How To Center a Div

[https://www.joshwcomeau.com/css/center-a-div/?utm_source=newsletter.reactdigest.net&utm_medium=newsletter&utm_campaign=how-to-center-a-div](https://www.joshwcomeau.com/css/center-a-div/?utm_source=newsletter.reactdigest.net&utm_medium=newsletter&utm_campaign=how-to-center-a-div)

> Contains code snippets
---

17. [x] ## Local Storage Api

[https://rxdb.info/articles/localstorage.html](https://rxdb.info/articles/localstorage.html)


```js
// Storing data using setItem
localStorage.setItem('username', 'john_doe');

// Retrieving data using getItem
const storedUsername = localStorage.getItem('username');

// Removing data using removeItem
localStorage.removeItem('username');

// Clearing all data
localStorage.clear();
```

### Understanding the Limitations of local storage

1. **Non-Async Blocking API**: One significant drawback is that js localStorage operates as a non-async blocking API. This means that any operations performed on localStorage can potentially block the main thread, leading to slower application performance and a less responsive user experience.

2. **Stringification Overhead**: Storing JSON data in localStorage requires stringifying the data before storage and parsing it when retrieved. This process introduces performance overhead, potentially slowing down operations by up to 10 times.

3. **Storage Limit**: Browsers typically impose a storage limit of around 5 MiB for each origin's localStorage.

------------------

18. [x] [https://semaphoreci.com/blog/htmx-react](https://semaphoreci.com/blog/htmx-react)  
