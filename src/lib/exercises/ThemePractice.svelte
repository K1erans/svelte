<script lang="ts">
  let darkMode = $state(false)

  const themeName = $derived(darkMode ? 'Dark' : 'Light')

  // TODO 1: Move this state into a Svelte store.
  // TODO 2: Read the store from another component.
  // TODO 3: Persist the chosen theme in localStorage.
</script>

<section class="exercise-card theme-practice" class:dark={darkMode} aria-labelledby="theme-title">
  <div>
    <p class="exercise-label">Exercise 04</p>
    <h3 id="theme-title">Theme practice</h3>
    <p>Learn boolean state, class directives, and eventually shared stores.</p>
  </div>

  <label class="toggle-row">
    <input type="checkbox" bind:checked={darkMode} />
    <span>{themeName} mode</span>
  </label>
</section>
