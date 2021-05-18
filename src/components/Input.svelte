<script>
  export let placeholder;
  export let handleClick;
  export let todo = '';
</script>

<div class="wrapper">
  <input type="text" {placeholder} bind:value={todo} />
  <button on:click={() => handleClick(todo)}>Add to-do</button>
</div>

<style>
  .wrapper {
    display: flex;
    justify-content: center;
  }

  input {
    height: 40px;
    width: 600px;

    font-size: 0.8rem;
    text-indent: 0.8rem;
  }
  button {
    height: 40px;
    width: 200px;
  }
</style>
