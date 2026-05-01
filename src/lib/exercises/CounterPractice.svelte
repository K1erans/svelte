<script lang="ts">
  let count = $state(0)

  function increase() {
    count += 1
  }

  // TODO 1: Add a decrease() function.
  // TODO 2: Add a reset() function.
  // TODO 3: Disable the minus button when count is 0.
</script>

<section class="exercise-card" aria-labelledby="counter-title">
  <div>
    <p class="exercise-label">Exercise 01</p>
    <h3 id="counter-title">Counter practice</h3>
    <p>Learn state, click events, and disabled button attributes.</p>
  </div>

  <div class="counter-workbench" aria-live="polite">
    <strong>{count}</strong>

    <div class="control-row">
      <button type="button" class="button button-secondary">Minus</button>
      <button type="button" class="button button-primary" onclick={increase}>Plus</button>
      <button type="button" class="button button-secondary">Reset</button>
    </div>
  </div>
</section>
