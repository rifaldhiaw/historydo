<script>
  import { faHome } from "@fortawesome/free-solid-svg-icons/faHome";
  import { faCalendarWeek } from "@fortawesome/free-solid-svg-icons/faCalendarWeek";
  import { faLayerGroup } from "@fortawesome/free-solid-svg-icons/faLayerGroup";

  import NavbarButton from "./NavbarButton.svelte";
  import { createEventDispatcher } from "svelte";

  import { NAV } from "../utils/constant";

  const dispatch = createEventDispatcher();

  export let currentNav = NAV.HOME;

  function changeNav(tab) {
    return function() {
      dispatch("changeNav", {
        value: tab
      });
    };
  }
</script>

<div
  class="w-full fixed bottom-0 left-0 bg-white shadow-md border-t-2
  border-gray-300 flex items-center">

  <NavbarButton
    isActive={currentNav === NAV.HOME}
    icon={faHome}
    on:click={changeNav(NAV.HOME)} />
  <NavbarButton
    isActive={currentNav === NAV.LIST}
    icon={faLayerGroup}
    on:click={changeNav(NAV.LIST)} />
  <NavbarButton
    isActive={currentNav === NAV.HISTORY}
    icon={faCalendarWeek}
    on:click={changeNav(NAV.HISTORY)} />
</div>
