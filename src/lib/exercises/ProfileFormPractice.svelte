<script lang="ts">
  let name = $state('')
  let email = $state('')
  let role = $state('Svelte beginner')

  const hasName = $derived(name.trim().length > 0)
  const hasEmail = $derived(email.includes('@'))
  const canSubmit = $derived(hasName && hasEmail)

  // TODO 1: Add an age field and show it in the preview.
  // TODO 2: Add a validation message when the email is invalid.
  // TODO 3: Handle submit and show a saved message.
</script>

<section class="exercise-card" aria-labelledby="profile-title">
  <div>
    <p class="exercise-label">Exercise 03</p>
    <h3 id="profile-title">Profile form practice</h3>
    <p>Learn input bindings, derived values, validation, and live previews.</p>
  </div>

  <form class="form-grid">
    <label>
      Name
      <input bind:value={name} placeholder="Ada Lovelace" />
    </label>

    <label>
      Email
      <input bind:value={email} placeholder="ada@example.com" />
    </label>

    <label>
      Role
      <input bind:value={role} />
    </label>

    <button type="button" class="button button-primary" disabled={!canSubmit}>
      Save profile
    </button>
  </form>

  <div class="preview-box">
    <strong>{name || 'Your name'}</strong>
    <span>{email || 'email@example.com'}</span>
    <span>{role}</span>
  </div>
</section>
