<script>
  import router from "page";

  import Home from "./pages/Home.svelte";
  import List from "./pages/List.svelte";
  import Project from "./pages/project/Project.svelte";

  import Navbar from "./components/Navbar.svelte";

  import { NAV } from "./utils/constant";

  let page;
  let params;
  let currentNav = NAV.HOME;

  router("/", () => {
    page = Home;
    currentNav = NAV.HOME;
  });
  router("/project/:id?", (ctx, next) => {
    params = { id: ctx.params.id };
    page = Project;
    currentNav = NAV.LIST;
  });
  router("/account", () => {
    page = List;
    currentNav = NAV.HISTORY;
  });
  router("*", () => {
    page = Home;
    currentNav = NAV.HOME;
  });
  router.start();
</script>

<main class="mb-48 ">
  <svelte:component this={page} {params} />
</main>

<Navbar {currentNav} />
