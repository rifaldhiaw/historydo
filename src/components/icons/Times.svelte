<script>
  import Icon from "fa-svelte";
  import { faTimes } from "@fortawesome/free-solid-svg-icons/faTimes";

  let className = "";
  export { className as class };
</script>

<div on:click class={'cursor-pointer ' + className}>
  <Icon icon={faTimes} class="text-gray-700" />
</div>
