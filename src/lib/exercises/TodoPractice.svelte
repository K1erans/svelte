<script lang="ts">
  type Todo = {
    id: number
    text: string
    done: boolean
  }

  let todos = $state<Todo[]>([
    { id: 1, text: 'Read a Svelte component', done: true },
    { id: 2, text: 'Update state from a button', done: false },
    { id: 3, text: 'Render a list with {#each}', done: false },
  ])

  function toggleTodo(id: number) {
    todos = todos.map((todo) =>
      todo.id === id ? { ...todo, done: !todo.done } : todo,
    )
  }

  // TODO 1: Add an input with bind:value for a new todo.
  // TODO 2: Add a form submit handler that appends a todo.
  // TODO 3: Add a delete button beside each todo.
  // TODO 4: Add all / active / done filters.
</script>

<section class="exercise-card" aria-labelledby="todo-title">
  <div>
    <p class="exercise-label">Exercise 02</p>
    <h3 id="todo-title">Todo list practice</h3>
    <p>Learn arrays, each blocks, checkbox state, and list updates.</p>
  </div>

  <ul class="todo-list">
    {#each todos as todo (todo.id)}
      <li class:done={todo.done}>
        <label>
          <input
            type="checkbox"
            checked={todo.done}
            onchange={() => toggleTodo(todo.id)}
          />
          <span>{todo.text}</span>
        </label>
      </li>
    {/each}
  </ul>
</section>
