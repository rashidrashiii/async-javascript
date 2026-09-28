# Async JavaScript (Callbacks → Promises → Async/Await)

**Live page:** https://rashidrashiii.github.io/async-javascript/

An interactive, single-page guide to asynchronous JavaScript. Every code example runs in the browser: press **Run** and the output appears next to the code, with a timestamp on each line so you can see *when* things happen.

## What's covered

1. **Why async?** How JavaScript handles slow tasks without freezing the page
2. **Callbacks** Simple callbacks and the error-first convention
3. **Callback hell** Why nested callbacks become hard to manage
4. **Promises** States, `resolve`/`reject`, `.then`/`.catch`/`.finally`, chaining, wrapping callback APIs
5. **Async/await** The syntax, `try`/`catch`/`finally`, error types, a real `fetch` request, top-level await
6. **Sequential vs parallel** Timing comparison and `Promise.all`
7. **Promise combinators** `Promise.all`, `allSettled`, `race` and `any`
8. **Error handling patterns** A `[data, error]` wrapper, default values, retry with exponential backoff
9. **Common mistakes** Missing `await`, `await` in a normal function, unhandled rejections, missing `return`
10. **Recap and practice** The same task written three ways, key terms, and practice tasks

## How to use

| Action | How |
|---|---|
| Run an example | Click **Run**, or press `Ctrl` + `Enter` (`Cmd` + `Enter` on Mac) while editing |
| Edit code | Click in any code panel and type. `Tab` inserts two spaces |
| Leave the editor | Press `Esc`, then `Tab` moves to the next control |
| Restore the original code | Click **Reset** |
| Clear the output | Click **Clear** |
| Change the text size | Use the **A+** / **A−** buttons in the sidebar (your choice is remembered) |

The dot in each output panel shows the state of the run using the Promise state colours:
amber means still running (pending), green means finished (fulfilled), and red means an error was never caught (rejected).

Many examples end with a **Try this** suggestion, such as changing `getBook(1)` to `getBook(-1)` to see the error path.

## Deploying to GitHub Pages

1. Create a new repository on GitHub (for example `async-javascript`).
2. Upload `index.html` and `README.md` to the root of the repository, either through **Add file → Upload files** on GitHub or with git:
   ```bash
   git init
   git add index.html README.md
   git commit -m "Add async JavaScript guide"
   git branch -M main
   git remote add origin https://github.com/rashidrashiii/async-javascript.git
   git push -u origin main
   ```
3. In the repository, open **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose the `main` branch and the `/ (root)` folder, then click **Save**.
5. After a minute or two the page is live at `https://rashidrashiii.github.io/async-javascript/`.

## Running it locally

No build step or install is needed. Just open `index.html` in any modern browser (Chrome, Edge, Firefox or Safari).

## Notes

- **Internet:** the page works offline except for the web fonts (it falls back to system fonts) and the *Loading a user from an API* example, which calls the free [JSONPlaceholder](https://jsonplaceholder.typicode.com) API.
- **Shared helpers:** examples from chapter 4 onward use `wait`, `getBook`, `getAuthor` and `getReviews`. These are defined once in the `<script id="library-helpers">` block and loaded automatically before any example marked with `data-helpers`. Each one waits about a second to imitate a network request.
- **How examples run:** code is run with an async function wrapper and a custom `console`, so output is shown on the page rather than in the browser's developer tools. Timers from a previous run are cancelled when you press **Run again**.

## Adding your own example

Add a block like this anywhere inside a chapter in `index.html`:

```html
<div class="example" data-title="My example" data-helpers>
<script type="text/plain" class="src">
async function main() {
  const book = await getBook(1);
  console.log(book.title);
}
main();
</script>
  <p class="try"><strong>Try this:</strong> an optional hint shown under the example.</p>
</div>
```

- `data-title` sets the heading above the example.
- `data-helpers` loads the shared library helpers (leave it out if the example defines its own functions).
- `data-static` shows code only, with no Run button or output panel.

## References

- [MDN: Using Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [MDN: async function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [JavaScript.info: Promises](https://javascript.info/promise-basics)
- [JavaScript.info: Async/await](https://javascript.info/async-await)
