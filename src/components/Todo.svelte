<script>
  export let todo;
  export let deleteTodo;
  export let completeTodo;
</script>

<div class="wrapper">
  <p class={`text ${todo.isComplete ? 'isComplete' : ''}`}>{todo.text}</p>
  <div>
    <button on:click={() => deleteTodo(todo)}>Delete Todo</button>
    <button on:click={() => completeTodo(todo)}>Complete Todo</button>
  </div>
</div>

<style>
  .wrapper {
    padding: 0px 16px;
    margin-bottom: 8px;
    height: 60px;

    display: flex;
    justify-content: space-between;
    align-items: center;

    border: 1px solid hsl(194, 6%, 56%);
    border-radius: 4px;
  }

  button,
  p {
    margin: 0;
  }

  .text {
    color: hsl(194, 6%, 28%);
  }

  .isComplete {
    text-decoration: line-through;
  }
</style>
