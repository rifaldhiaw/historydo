<script>
  import Icon from "fa-svelte";
  import { faEllipsisV } from "@fortawesome/free-solid-svg-icons/faEllipsisV";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let name;
  export let useAction = false;
  let nameEl;

  const handleAction = () => dispatch("action");
  const handleBlurName = () => dispatch("rename", newName);
  const handleEnterName = e => {
    if (e.key === "Enter" || e.key === "Escape") {
      nameEl.blur();
    }
  };
</script>

<style>
  .buttonPos {
    bottom: -0.5rem;
  }
</style>

<div
  class="rounded-lg border-2 border-gray-400 bg-white p-3 pb-8 mb-10"
  on:click>
  <div class="flex justify-between items-center px-2">
    <h2
      bind:this={nameEl}
      bind:innerHTML={name}
      contenteditable="true"
      on:blur={handleBlurName}
      on:keypress={handleEnterName}>
      {name}
    </h2>
    <slot name="option" />
  </div>
  <hr />
  <div class="pt-3">
    <slot />
  </div>

  {#if useAction}
    <div class="flex justify-center h-0" on:click={handleAction}>
      <div
        class="w-12 h-12 rounded-full bg-white flex justify-center items-center
        relative buttonPos border-2 border-gray-400 hover:shadow-md
        cursor-pointer">
        <slot name="action" class="flex-1" />
      </div>
    </div>
  {/if}
</div>
