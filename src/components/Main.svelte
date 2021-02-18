<script lang="ts">
  import { fix_position } from "svelte/internal";

  import Darkmode from "./Darkmode.svelte";

  let todoList = [];
  let title: string = "";
  let description: string = "";

  function addTodo() {
    if (title !== "") {
      todoList = [...todoList, { title: title, description: description }];
      title = "";
      description = "";
    }
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
          <li class="todo">
            <div>
              <span on:click={() => removeTodo(index)}>🗑</span>
            </div>
            <div>
              TODO: {todo.title} <br /> NOTE: {todo.description}
            </div>
          </li>
        {/each}
      </ul>
    </div>
    <Darkmode />
  </main>
{:else}
  <main>
    <div class="message form">
      <p>
        Please complete at least one of your <br /> current tasks before adding more!
      </p>
      <ul>
        {#each todoList as todo, index}
          <li>
            <span on:click={() => removeTodo(index)}>🗑</span>
            TODO: {todo.title} <br /> NOTE: {todo.description}
          </li>
        {/each}
      </ul>
    </div>
    <Darkmode />
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
    height: 28rem;
    width: 25rem;
    background-color: #e9e9e9;
    border-radius: 5px;
    opacity: 0.9;
    box-shadow: 0.5rem 0.5rem 0.5rem 1px rgba(0, 0, 0, 0.2);
  }

  .todo {
    display: flex;
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
    max-width: 20rem;
    color: #333;
  }

  span {
    margin-right: 1rem;
  }

  @media (max-width: 500px) {
    .form {
      width: 20rem;
      box-shadow: none;
    }
  }
</style>
