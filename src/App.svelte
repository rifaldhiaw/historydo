<script>
  import Home from "./pages/Home.svelte";
  import List from "./pages/List.svelte";
  import Navbar from "./components/Navbar.svelte";

  let currentPage = "home";

  function handleChangeTab(event) {
    console.log(event);
    currentPage = event.detail.value;
  }
</script>

<main class="mb-48 ">
  {#if currentPage == 'home'}
    <Home />
  {:else if currentPage == 'list'}
    <List />
  {:else}
    <div />
  {/if}
</main>

<Navbar on:changeTab={handleChangeTab} />
