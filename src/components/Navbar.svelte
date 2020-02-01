<script>
  import { faLayerGroup } from "@fortawesome/free-solid-svg-icons/faLayerGroup";
  import { faCalendarWeek } from "@fortawesome/free-solid-svg-icons/faCalendarWeek";
  import { faUser } from "@fortawesome/free-solid-svg-icons/faUser";

  import NavbarButton from "./NavbarButton.svelte";
  import { createEventDispatcher } from "svelte";

  import { NAV } from "../utils/constant";

  export let currentNav = NAV.HOME;
</script>

<div
  class="w-full fixed bottom-0 left-0 bg-white shadow-md border-t-2
  border-gray-300 flex items-center">

  <NavbarButton
    isActive={currentNav === NAV.HOME}
    icon={faCalendarWeek}
    path="/" />
  <NavbarButton
    isActive={currentNav === NAV.LIST}
    icon={faLayerGroup}
    path="/project" />
  <NavbarButton
    isActive={currentNav === NAV.HISTORY}
    icon={faUser}
    path="/account" />
</div>
