<script>
  import Icon from "fa-svelte";
  import { faPen } from "@fortawesome/free-solid-svg-icons/faPen";

  let className = "";
  export { className as class };
</script>

<div on:click class={'cursor-pointer ' + className}>
  <Icon icon={faPen} class="text-gray-700" />
</div>
