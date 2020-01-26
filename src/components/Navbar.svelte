<script>
  import { faHome } from "@fortawesome/free-solid-svg-icons/faHome";
  import { faCalendarWeek } from "@fortawesome/free-solid-svg-icons/faCalendarWeek";
  import { faLayerGroup } from "@fortawesome/free-solid-svg-icons/faLayerGroup";

  import NavbarButton from "./NavbarButton.svelte";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function changeTab(tab) {
    return function() {
      dispatch("changeTab", {
        value: tab
      });
    };
  }
</script>

<div
  class="w-full fixed bottom-0 left-0 bg-white shadow-md border-t-2
  border-gray-300 flex items-center">

  <NavbarButton icon={faHome} on:click={changeTab('home')} />
  <NavbarButton icon={faLayerGroup} on:click={changeTab('list')} />
  <NavbarButton icon={faCalendarWeek} on:click={changeTab('history')} />
</div>
