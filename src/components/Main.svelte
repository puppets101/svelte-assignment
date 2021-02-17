<script lang="ts">
  let todoList = [];
  let title: string = "";
  let description: string = "";

  function addTodo() {
    todoList = [...todoList, { title: title, description: description }];
    title = "";
    description = "";
  }

  function removeTodo(todo: number) {
    todoList.splice(todo, 1);
    todoList = todoList;
  }
</script>

{#if todoList.length <= 3}
  <main>
    <div class="form">
      <label for="title">TODO:</label>
      <input type="text" bind:value={title} />
      <label for="description">NOTE:</label>
      <input type="text" bind:value={description} />
      <br />
      <button on:click={addTodo}>Add Todo</button>
      <br />
      <ul>
        {#each todoList as todo, index}
          <li class="card">
            <span on:click={() => removeTodo(index)}>🗑</span>
            TODO: {todo.title} <br /> NOTE: {todo.description}
          </li>
        {/each}
      </ul>
    </div>
  </main>
{:else}
  <main>
    <div class="message form">
      <p>
        "Please complete at least one of your <br /> current tasks before adding
        more!"
      </p>
      <ul>
        {#each todoList as todo, index}
          <li class="card">
            <span on:click={() => removeTodo(index)}>🗑</span>
            TODO: {todo.title} <br /> NOTE: {todo.description}
          </li>
        {/each}
      </ul>
    </div>
  </main>
{/if}

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .form {
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 30rem;
    width: 25rem;
    background-color: #e9e9e9;
    border-radius: 5px;
  }

  .message {
    text-align: center;
  }

  .message p {
    margin-top: 4rem;
  }

  label {
    margin: 0.625rem;
    font-size: 1.25rem;
  }

  input {
    width: 18rem;
    outline: none;
  }

  button {
    width: 12rem;
    border-radius: 5px;
    transition: all 1s;
  }

  button:hover {
    background-color: cadetblue;
    cursor: pointer;
  }

  ul {
    padding-inline-start: 0;
  }

  li {
    position: relative;
    list-style: none;
    margin-top: 0.625rem;
    font-weight: bold;
  }

  span {
    display: inline-block;
    margin-right: 1rem;
  }

  .card {
    color: #333;
    padding: 0.5rem;
  }
</style>
