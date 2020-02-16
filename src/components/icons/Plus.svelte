<script>
  import Icon from "fa-svelte";
  import { faPlus } from "@fortawesome/free-solid-svg-icons/faPlus";

  let className = "";
  export { className as class };
</script>

<div on:click class={'cursor-pointer ' + className}>
  <Icon icon={faPlus} class="text-gray-700" />
</div>
