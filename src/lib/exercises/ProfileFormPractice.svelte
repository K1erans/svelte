<script lang="ts">
  let name = $state('')
  let email = $state('')
  let role = $state('Svelte beginner')

  const hasName = $derived(name.trim().length > 0)
  const hasEmail = $derived(email.includes('@'))
  const canSubmit = $derived(hasName && hasEmail)

  // TODO 1: Add an age field and show it in the preview.
  let age = $state('')
  // TODO 2: Add a validation message when the email is invalid.
    const emailError = $derived(
      hasEmail && email.trim().length === 0 ? '' : 'Please enter a valid email address.'
    )
  // TODO 3: Handle submit and show a saved message.
  function handleSubmit() {
    alert('Profile saved!')
  }
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
      {#if emailError}
        <span class="error-message">{emailError}</span>
      {/if}
    </label>

    <label>
      Age
      <input bind:value={age} placeholder="67" />
    </label>

    <label>
      Role
      <input bind:value={role} />
    </label>

    {#if canSubmit}
         <button type="button" class="button button-primary"  onclick={handleSubmit}>
          Save profile
        </button> 
    {/if}
  </form>

  <div class="preview-box">
    <strong>{name || 'Your name'}</strong>
    <span>{email || 'email@example.com'}</span>
    <span>{role}</span>
  </div>
</section>
