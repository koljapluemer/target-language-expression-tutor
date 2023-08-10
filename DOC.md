## Structure

I set this up as barebones skeleton SvelteKit. This is my first serious run with Svelte, so expect some weird setup.

Everything essentially lives in `+pages.svelte`. The tab structure is a combination of sleek DaisyUI stuff, and very simple page-counter & conditional display svelte logic. Svelte binding etc is gloriously terse, so there is actually not much logic...it's just card after card, with quite a lot of structural HTML and occasional logic references to the script at the top. Longest logic is the function to copy the chatGPT prompt and open chatGPT (`copy()`).

## History

### 2022-08-03

Lates Attempt: Trying to get a tabbed layout running. Metro UI was not fun, Tailwind was installed with some hassle, DaisyUI didn't work but probably will now that I updated node. Tried my hands on Flowbite because it has there [tabs](https://flowbite-svelte.com/docs/components/tab) but no luck yet.

Nevermind got DaisyUI running (sort of). Think will build the tab stuff per hand (don't even need tabs per se, more like breadcrumbs. Anyways, sketch UI, see todo)