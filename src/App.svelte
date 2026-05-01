<script lang="ts">
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from './assets/vite.svg'
  import heroImg from './assets/hero.png'
  import CounterPractice from './lib/exercises/CounterPractice.svelte'
  import ProfileFormPractice from './lib/exercises/ProfileFormPractice.svelte'
  import ThemePractice from './lib/exercises/ThemePractice.svelte'
  import TodoPractice from './lib/exercises/TodoPractice.svelte'

  type Task = {
    id: string
    day: string
    title: string
    goal: string
    concepts: string[]
    practice: string
  }

  let completed = $state<string[]>([])

  const learningTasks: Task[] = [
    {
      id: 'component-basics',
      day: 'Task 01',
      title: 'Edit your first component',
      goal: 'Change the page title, button text, and one visual section in src/App.svelte.',
      concepts: ['Svelte files', 'markup', 'imports'],
      practice: 'Replace this learning dashboard heading with your own project idea.',
    },
    {
      id: 'state-events',
      day: 'Task 02',
      title: 'Build a tiny counter',
      goal: 'Create a number with $state and update it from a button click.',
      concepts: ['$state', 'events', 'onclick'],
      practice: 'Add plus, minus, and reset buttons, then disable minus at zero.',
    },
    {
      id: 'conditional-ui',
      day: 'Task 03',
      title: 'Show conditional messages',
      goal: 'Render different text based on whether a task is complete.',
      concepts: ['{#if}', '{:else}', 'boolean state'],
      practice: 'Show a progress message when at least three tasks are checked off.',
    },
    {
      id: 'lists-each',
      day: 'Task 04',
      title: 'Render data with each blocks',
      goal: 'Move repeated UI into an array and render it with {#each}.',
      concepts: ['arrays', '{#each}', 'keys'],
      practice: 'Add two more tasks to the learningTasks array and make them appear automatically.',
    },
    {
      id: 'props-components',
      day: 'Task 05',
      title: 'Extract a task card component',
      goal: 'Move one repeated card into src/lib/TaskCard.svelte and pass data into it.',
      concepts: ['components', 'props', '$props'],
      practice: 'Keep the checkbox behavior working after extracting the component.',
    },
    {
      id: 'derived-progress',
      day: 'Task 06',
      title: 'Calculate progress',
      goal: 'Use derived values to calculate completion percent from checked tasks.',
      concepts: ['$derived', 'computed UI', 'progress'],
      practice: 'Replace the hard-coded progress bar width with a derived percentage.',
    },
    {
      id: 'forms-bindings',
      day: 'Task 07',
      title: 'Add your own task form',
      goal: 'Use input bindings to collect a title and append it to a task list.',
      concepts: ['bind:value', 'forms', 'array updates'],
      practice: 'Create a simple form that adds custom study tasks below this roadmap.',
    },
    {
      id: 'capstone',
      day: 'Task 08',
      title: 'Build a mini study tracker',
      goal: 'Combine state, lists, components, events, and conditional rendering in one feature.',
      concepts: ['composition', 'state design', 'polish'],
      practice: 'Track topics, notes, completion, and a filter for all, active, and done.',
    },
  ]

  const totalTasks = learningTasks.length
  const completedCount = $derived(completed.length)
  const progress = $derived(Math.round((completedCount / totalTasks) * 100))

  function toggleTask(taskId: string) {
    completed = completed.includes(taskId)
      ? completed.filter((id) => id !== taskId)
      : [...completed, taskId]
  }
</script>

<main class="shell">
  <nav class="nav" aria-label="Main navigation">
    <a class="brand" href="/" aria-label="Svelte Studio home">
      <span class="brand-mark">
        <img src={svelteLogo} alt="" />
      </span>
      <span>Svelte Studio</span>
    </a>

    <div class="nav-actions" aria-label="Project links">
      <a href="https://svelte.dev/tutorial" target="_blank" rel="noreferrer">Tutorial</a>
      <a href="https://svelte.dev/docs" target="_blank" rel="noreferrer">Docs</a>
      <a class="button button-ghost" href="https://vite.dev/guide/" target="_blank" rel="noreferrer">Vite</a>
    </div>
  </nav>

  <section class="hero learning-hero" aria-labelledby="page-title">
    <div class="hero-copy">
      <p class="eyebrow">Svelte learning plan</p>
      <h1 id="page-title">Eight practical tasks to learn Svelte by building.</h1>
      <p class="lede">
        Work through these in order. Each task asks you to change this app, so you learn the framework inside a real project instead of reading passively.
      </p>

      <div class="actions">
        <a class="button button-primary" href="#tasks">Start task 01</a>
        <a class="button button-secondary" href="https://svelte.dev/tutorial" target="_blank" rel="noreferrer">
          Open tutorial
        </a>
      </div>

      <dl class="metrics" aria-label="Learning progress">
        <div>
          <dt>Tasks done</dt>
          <dd>{completedCount}/{totalTasks}</dd>
        </div>
        <div>
          <dt>Progress</dt>
          <dd>{progress}%</dd>
        </div>
        <div>
          <dt>Focus</dt>
          <dd>Core</dd>
        </div>
      </dl>
    </div>

    <div class="hero-visual learning-card" aria-label="Current study status">
      <div class="visual-header">
        <span></span>
        <span></span>
        <span></span>
      </div>
      <div class="visual-stage study-stage">
        <img class="base" src={heroImg} alt="" />
        <img class="logo svelte" src={svelteLogo} alt="Svelte" />
        <img class="logo vite" src={viteLogo} alt="Vite" />
        <div class="code-note">
          <span>today.svelte</span>
          <strong>{completedCount === totalTasks ? 'Capstone ready' : learningTasks[completedCount]?.title}</strong>
        </div>
      </div>
      <div class="status-row">
        <span>{completedCount === totalTasks ? 'Complete' : 'In progress'}</span>
        <strong>{totalTasks - completedCount} tasks remaining</strong>
      </div>
    </div>
  </section>

  <section id="tasks" class="panel learning-panel" aria-labelledby="tasks-title">
    <div class="section-heading">
      <div>
        <p class="eyebrow">Roadmap</p>
        <h2 id="tasks-title">Your Svelte practice queue</h2>
      </div>

      <div class="progress-box" aria-label={`${progress}% complete`}>
        <span>{progress}% complete</span>
        <div class="progress-track">
          <div class="progress-fill" style={`width: ${progress}%`}></div>
        </div>
      </div>
    </div>

    <div class="task-grid">
      {#each learningTasks as task (task.id)}
        <article class="task-card" class:complete={completed.includes(task.id)}>
          <label class="task-check">
            <input
              type="checkbox"
              checked={completed.includes(task.id)}
              onchange={() => toggleTask(task.id)}
            />
            <span>{task.day}</span>
          </label>

          <h3>{task.title}</h3>
          <p>{task.goal}</p>

          <div class="concepts" aria-label="Concepts covered">
            {#each task.concepts as concept}
              <span>{concept}</span>
            {/each}
          </div>

          <div class="practice">
            <strong>Practice</strong>
            <p>{task.practice}</p>
          </div>
        </article>
      {/each}
    </div>
  </section>

  <section class="panel exercises-panel" aria-labelledby="exercises-title">
    <div class="section-heading">
      <div>
        <p class="eyebrow">Starter files</p>
        <h2 id="exercises-title">Practice area</h2>
      </div>

      <span class="file-pill">LEARNING_TASKS.md</span>
    </div>

    <div class="exercise-grid">
      <CounterPractice />
      <TodoPractice />
      <ProfileFormPractice />
      <ThemePractice />
    </div>
  </section>
</main>
