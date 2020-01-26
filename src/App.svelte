<script>
  import Home from "./pages/Home.svelte";
  import List from "./pages/List.svelte";
  import Navbar from "./components/Navbar.svelte";

  import { NAV } from "./utils/constant";

  let currentNav = NAV.HOME;

  function handleChangeNav(event) {
    currentNav = event.detail.value;
  }
</script>

<main class="mb-48 ">
  {#if currentNav == NAV.HOME}
    <Home />
  {:else if currentNav == NAV.LIST}
    <List />
  {:else}
    <div />
  {/if}
</main>

<Navbar on:changeNav={handleChangeNav} {currentNav} />
