<script>
  import Icon from "fa-svelte";
  import { faCheck } from "@fortawesome/free-solid-svg-icons/faCheck";

  let className = "";
  export { className as class };
</script>

<div on:click class={'cursor-pointer ' + className}>
  <Icon icon={faCheck} class="text-gray-700" />
</div>
