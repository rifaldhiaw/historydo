<script>
  import Icon from "fa-svelte";
  import { faEllipsisV } from "@fortawesome/free-solid-svg-icons/faEllipsisV";

  let className = "";
  export { className as class };
</script>

<!-- REVIEW cursor -->
<div on:click class={'cursor-pointer ' + className}>
  <Icon icon={faEllipsisV} class="text-gray-700" />
</div>
