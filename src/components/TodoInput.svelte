<script>
  import Icon from "fa-svelte";
  import { faPlusCircle } from "@fortawesome/free-solid-svg-icons/faPlusCircle";
</script>

<style>
  .inputTodo {
    bottom: 4rem;
    left: 0;
  }
</style>

<div class="fixed flex inputTodo w-full py-2 px-5 bg-white items-center">
  <input
    type="text"
    class="bg-gray-100 border border-gray-400 rounded-full cursor-text w-full
    h-10 mx-2" />
  <Icon icon={faPlusCircle} class="text-3xl mx-2" />
</div>
