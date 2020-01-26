<script>
  import Icon from "fa-svelte";

  export let icon;
</script>

<div
  class="flex justify-center items-center cursor-pointer h-16 flex-1"
  on:click>
  <Icon {icon} class="text-3xl" />
</div>
