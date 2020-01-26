<script>
  import Icon from "fa-svelte";

  export let icon;
  export let isActive = false;

  $: activeStyle = isActive ? " text-blue-600" : "text-gray-600";
</script>

<div
  class={'flex justify-center items-center cursor-pointer h-16 flex-1 ' + activeStyle}
  on:click>
  <Icon {icon} class="text-3xl" />
</div>
