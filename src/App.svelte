<script lang="ts">
  import Header from "./components/Header.svelte";
  import Main from "./components/Main.svelte";
</script>

<div class="container">
  <Header />
  <Main />
</div>

<style>
  :global(body) {
    background-color: #f4f4f4;
    color: cadetblue;
    transition: background-color 0.3s;
  }
  :global(body.dark-mode) {
    background-color: #112331;
    color: cadetblue;
  }
</style>
