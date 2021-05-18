<script lang="ts">
  import type { TodoStructure } from './types/Todo';
  import Input from './components/Input.svelte';
  import Todo from './components/Todo.svelte';

  const placeholder = 'Write your to-do here';
  let text: string;

  export let arrayOfTodos: TodoStructure[] = [];

  function handleClick(todo: string) {
    arrayOfTodos = [...arrayOfTodos, { text: todo }];
    text = '';
  }

  function deleteTodo(todoToDelete: TodoStructure) {
    arrayOfTodos = [
      ...arrayOfTodos.filter((todo) => todo.text !== todoToDelete.text),
    ];
  }

  function completeTodo(todoToComplete: TodoStructure) {
    const updatedArray = arrayOfTodos.map((todo) => {
      if (todo.text === todoToComplete.text) {
        return { ...todo, isComplete: true };
      }
      return todo;
    });
    arrayOfTodos = updatedArray;
    console.log(arrayOfTodos);
  }
</script>

<div class="wrapper">
  <header>
    <h1>Svelte To-do App</h1>
    <p>An app to try out Svelte</p>
  </header>
  <main>
    <Input bind:todo={text} {placeholder} {handleClick} />
    <div class="todosContainer">
      {#each arrayOfTodos as todo}
        <Todo {todo} {deleteTodo} {completeTodo} />
      {/each}
    </div>
  </main>
</div>

<style>
  .wrapper {
    max-width: 500px;
    margin: 0 auto;
  }

  header {
    text-align: center;
    padding: 1em;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 2em;
    font-weight: 300;
  }

  .todosContainer {
    margin-top: 16px;
  }
</style>
