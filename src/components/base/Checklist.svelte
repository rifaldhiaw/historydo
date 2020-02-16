<script>
  import { createEventDispatcher } from "svelte";
  import Times from "../icons/Times.svelte";
  const dispatch = createEventDispatcher();

  export let isFinished;
  export let value;
  let isEditMode = false;

  const handleEnter = e => {
    if (e.key === "Enter" || e.key === "Escape") {
      dispatch("edited", value);
      isEditMode = false;
    }
  };
</script>

<style>
  .times {
    right: 1rem;
    top: 0.5rem;
  }
</style>

<div class="px-5 py-2 w-full flex items-center text-gray-700">
  <input type="checkbox" name={value} bind:checked={isFinished} class="mr-2" />
  {#if isEditMode}
    <div class="w-full relative">
      <!-- svelte-ignore a11y-autofocus -->
      <input
        class="appearance-none border-2 rounded w-full py-2 px-3 leading-tight
        focus:outline-none"
        id="todo"
        bind:value
        autofocus
        on:keypress={handleEnter}
        on:blur={() => (isEditMode = false)}
        type="text" />

      <div
        class="absolute times"
        on:mousedown|preventDefault={() => dispatch('remove')}>
        <Times class="text-gray-400" />
      </div>
    </div>
  {:else}
    <div on:click={() => (isEditMode = true)} class="flex-1">{value}</div>
  {/if}
</div>
