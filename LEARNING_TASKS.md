# Svelte Learning Tasks

Run the app with:

```sh
npm run dev
```

Then work through these files in order:

1. `src/lib/exercises/CounterPractice.svelte`
   - Add minus and reset behavior.
   - Disable minus when the count is `0`.

2. `src/lib/exercises/TodoPractice.svelte`
   - Add a todo form.
   - Delete todos.
   - Add all / active / done filters.

3. `src/lib/exercises/ProfileFormPractice.svelte`
   - Add an age field.
   - Show validation messages.
   - Show a saved message after submit.

4. `src/lib/exercises/ThemePractice.svelte`
   - Move theme state into a Svelte store.
   - Read the same state from another component.
   - Save the selected theme to `localStorage`.

5. `src/App.svelte`
   - Extract the roadmap task cards into a reusable component.
   - Add two extra tasks to the `learningTasks` array.
   - Replace the hero copy with your own app idea.

Use `npm run check` after each task to catch Svelte and TypeScript mistakes.
