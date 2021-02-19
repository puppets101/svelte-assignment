<script lang="ts">
  let darkMode: boolean = false;

  function toggleBackground() {
    window.document.body.classList.toggle("dark-mode");

    if (darkMode) {
      darkMode = false;
    } else if (!darkMode) {
      darkMode = true;
    }
  }
</script>

<button on:click={toggleBackground}>
  {darkMode ? "LIGHT MODE" : "DARK MODE"}
</button>

<style>
  button {
    background-color: cadetblue;
    color: white;
    border: none;
    width: 8rem;
    margin-top: 2rem;
    border-radius: 5px;
    padding: 0.5rem;
    transition: all 1s;
  }

  button:hover {
    background-color: #112331;
  }

  :global(body.dark-mode) button:hover {
    background-color: #f4f4f4;
    color: cadetblue;
  }
</style>
