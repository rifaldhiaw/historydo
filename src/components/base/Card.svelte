<script>
  import Icon from "fa-svelte";
  import { faEllipsisV } from "@fortawesome/free-solid-svg-icons/faEllipsisV";

  export let name;
  export let onAction = null;
</script>

<div class="rounded-lg border-2 border-gray-400 bg-white p-3 mb-5" on:click>
  <div class="flex justify-between items-center px-2">
    <h2>{name}</h2>
    {#if onAction}
      <div on:click={onAction} class="cursor-pointer">
        <Icon icon={faEllipsisV} class="text-gray-700" />
      </div>
    {/if}
  </div>
  <hr />
  <div class="pt-3">
    <slot />
  </div>
</div>
