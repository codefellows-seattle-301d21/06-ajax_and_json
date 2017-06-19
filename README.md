![CF](https://i.imgur.com/7v5ASc8.png)  Lab 06: AJAX and JSON
=======
[Code of Conduct](https://github.com/codefellows/code-of-conduct)

## Submission Instructions
When you are finished with lab, follow these steps to submit your work. Create one Pull Request (aka: "PR") from your Forked repo to the CF repo with your changes, and you'll each submit that same PR link in Canvas.

1. Ensure that all your local changes are committed, and pushed to your origin repo.
1. Visit the origin repo on github.com, and ensure that all of your completed work has been merged to master via Pull Requests within your repo.
1. Create a new PR from your Fork to the CF repo and ensure the branches look correct.
1. Fill in the template based on the text box prompts:
  1. Write a good descriptive summary of your changes:
    1. Be sure to include how much time you spent on it, and who you worked with.
    1. Briefly reflect on and summarize your process.
1. When you create the PR, it will have a unique URL. Copy this link, share with your partner, and paste it into the assignment submission form in Canvas. Both the driver and the navigator will submit the same PR link.
---

## Learning Objectives
* Identify when apps need persistence, to improve the UX and isolate the model logic in the code base.
* Understand how the browser uses the request-response (WRRC) cycle to render an HTML file or AJAX call.
  * Review the use of jQuery's Deferred Object (`$.get().then().catch()`)
* Refresh the localStorage object and JSON usage
* Understand the implementation and usage of ES2015 Syntax for `let` and `const`

---

## Resources  
[MDN let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
[MDN const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)
[jQuery API Reference (see AJAX Methods and the far right)](https://oscarotero.com/jquery/)

---

## Feature Tasks  
1. Start by looking over what's new in the codebase. There is a /data folder! There are some `// REVIEW` comments! Practice your code-reading skills.
1. In `index.html`, after we load all our script tags, we need to kick off the retrieval of data, and rendering of the page. What's the right method to call?
1. Fill in what's needed in article.js, so that all the articles are loaded and rendered, and retrieved with AJAX.
1. Actually, we only need to request the JSON file when we don't already have it, so the conditional check should only do the AJAX call when localStorage doesn't have the rawData yet.

#### Stretch Goals
1. Coded as above, we won't request a new JSON file if we've already downloaded it once. This caching is problematic: if the JSON file is updated (therefore our cache is "invalid"), a new copy won't be requested from the server unless localStorage is cleared. To overcome this, we could use a small and fast AJAX request with a method of `HEAD`, to request just the headers, and not the contents of the file. The HEAD response will contain a key called "eTag". The value of the eTag header is calculated based on the contents of the file. So if a new article is added (or an existing one is edited even slightly), the eTag will be different.
  - If we cache the eTag, then we can compare our cached version of it with a new eTag check, to determine if we need to get the whole file or not.
  - This can introduce some synchronicity issues, so we'll need to carefully control what methods are calling back to what.

Hint: You'll be able to see everything the server returns, if your AJAX success function looks something like this:

```javascript
function(data, message, xhr) {
  console.log(xhr);
}
```

---

## Rubric  
Criteria | Pts
---|---
Meets all Assignment Reqs | 6
Uses idiomatic code style | 3
Follows proper Git workflow | 1
**Total** | **10**
