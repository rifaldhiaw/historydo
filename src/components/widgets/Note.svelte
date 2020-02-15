<script>
  import Card from "../../components/base/Card.svelte";
  import Editor from "../../components/Editor.svelte";
  import Edit from "../../components/icons/Edit.svelte";
  import Check from "../../components/icons/Check.svelte";
  import showdown from "showdown";

  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let value = "";
  let isEdit = false;
  let converter = new showdown.Converter();
  $: htmlValue = converter.makeHtml(value);

  const handleClick = () => alert("on click card option");
  const handleEdit = () => {
    isEdit = !isEdit;
    if (!isEdit) {
      dispatch("change", value);
    }
  };
  const handleChange = e => {
    value = e.detail;
  };
</script>

<div class="mb-5">
  <Card name="Note" useOption="true" on:optionClick={handleClick}>
    <div slot="action" class="mr-4" on:click={handleEdit}>
      {#if isEdit}
        <Check />
      {:else}
        <Edit />
      {/if}
    </div>
    {#if isEdit}
      <Editor {value} on:change={handleChange} />
    {:else}
      <div class="px-2">
        {@html htmlValue}
      </div>
    {/if}
  </Card>
</div>
