<script>
  import router from "page";
  import Home from "./pages/Home.svelte";
  import Project from "./pages/project/Project.svelte";
  import Navbar from "./components/Navbar.svelte";
  import { NAV } from "./utils/constant";
  import { FirebaseApp, User, Doc, Collection } from "sveltefire";

  import firebase from "firebase/app";
  import "firebase/firestore";
  import "firebase/auth";
  import "firebase/performance";
  import "firebase/analytics";

  const firebaseConfig = {
    apiKey: "AIzaSyAZ28QgYill-87LCLAMEAsEYH-T1yRSB6Q",
    authDomain: "manager-dev-6e242.firebaseapp.com",
    databaseURL: "https://manager-dev-6e242.firebaseio.com",
    projectId: "manager-dev-6e242",
    storageBucket: "manager-dev-6e242.appspot.com",
    messagingSenderId: "339640897285",
    appId: "1:339640897285:web:92f5844a0ab275ae35716c",
    measurementId: "G-RNG6632WHF"
  };

  firebase.initializeApp(firebaseConfig);

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
    page = Home;
    currentNav = NAV.HISTORY;
  });
  router("*", () => {
    page = Home;
    currentNav = NAV.HOME;
  });
  router.start();
</script>

<FirebaseApp {firebase}>

  <main class="mb-48 ">
    <svelte:component this={page} {params} />
  </main>

  <Navbar {currentNav} />
</FirebaseApp>
