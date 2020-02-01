<script>
  import Icon from "fa-svelte";

  export let icon;
  export let isActive = falsei;
  export let path = "/";

  $: activeStyle = isActive ? " text-gray-700" : "text-gray-500";
</script>

<a
  href={path}
  class={'flex justify-center items-center cursor-pointer h-16 flex-1 ' + activeStyle}>
  <Icon {icon} class="text-3xl" />
</a>
