<script>
  import Option from "../icons/Option.svelte";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let values;
  export let width = "10";
  let isVisible = false;

  const handleWindowClick = e => {
    if (!e.target.matches("svg") && !e.target.matches("path"))
      isVisible = false;
  };
</script>

<svelte:window on:click={handleWindowClick} />
<div class="relative">
  <div
    class="h-10 w-10 flex justify-center items-center"
    on:click={() => (isVisible = true)}
    on:blur={() => (isVisible = false)}>
    <Option />
  </div>

  {#if isVisible}
    <div
      class="z-10 absolute top-0 right-0 bg-white shadow-md"
      style="width: {width}rem">
      {#each values as val, i (val.value)}
        {#if val.type === 'primary'}
          <div
            on:click={() => dispatch('select', val.value)}
            class="px-3 py-2 hover:bg-gray-200 cursor-pointer">
            {val.text}
          </div>
        {:else if val.type === 'danger'}
          <div
            on:click={() => dispatch('select', val.value)}
            class="px-3 py-2 hover:bg-gray-200 cursor-pointer text-red-400">
            {val.text}
          </div>
        {:else}
          <div class="border-b-2" />
        {/if}
      {/each}
    </div>
  {/if}
</div>
