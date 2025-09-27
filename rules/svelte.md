**Development Philosophy:**

- Always use Svelte 5 runes syntax - never fall back to legacy Svelte 4 patterns
- Prioritize clean, readable code over clever solutions
- Favor pragmatic, simple implementations
- Maintain clear separation of concerns between components
- Write self-documenting code with meaningful variable and function names

**Required Actions:**

Before working on any Svelte/SvelteKit task, you MUST read the distilled Svelte documentation at https://svelte.dev/llms-medium.txt.

**Svelte/Sveltekit Rules:**

- Be careful with using `{#await}` blocks.
  - This is because Svelte rerenders all content when the promise changes, even if the promise result ends up being the same. If the content depends directly on the results instead of the promise, and the result ends up being the same after an update, the content won't rerender/remount, avoiding unnecessary rerenders.
- Do not rely on deep dependency tracking with `$effect` and `$derived`. Use `untrack` liberally to be safe.
- Avoid using shallow routing.
- When passing functions to event handlers, always wrap them in array functions. For example, instead of `<button onclick={test.toggle}>Broken Toggle</button>`, use `<button onclick={() => test.toggle()}>Working Toggle</button>`.
- Always use runes mode. Globally enforce Runes mode in the Svelte compiler. Otherwise components that are not explicitly using runes are treated as legacy and wont track imported runes, leading to unexpected behavior. Make sure you don't accidentally fall back to deprecated Svelte 4 syntax.
- Consult the Svelte 5 and SvelteKit documentations for any questions.

**When Creating Components:**

- Start with a clear component interface (props, events, slots)
- Implement proper TypeScript typing
- Structure components for reusability and maintainability
- Add inline comments for complex logic or non-obvious patterns

**Vite Rules:**

- When using environmental variables inside of the Vite application, import them from `$env/static/private` and `$env/static/public`.
