<script>
  import Icon from "fa-svelte";
  import { faEllipsisV } from "@fortawesome/free-solid-svg-icons/faEllipsisV";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let name;
  export let useOption = false;
</script>

<div
  class="rounded-lg border-2 border-gray-400 bg-white p-3 pb-8 mb-5"
  on:click>
  <div class="flex justify-between items-center px-2">
    <h2>{name}</h2>
    {#if useOption}
      <div class="flex">
        <slot name="action" />
        <div on:click={() => dispatch('optionClick')} class="cursor-pointer">
          <Icon icon={faEllipsisV} class="text-gray-700" />
        </div>
      </div>
    {/if}
  </div>
  <hr />
  <div class="pt-3">
    <slot />
  </div>
</div>
