<script>
  import Card from "../../components/base/Card.svelte";
  import Menu from "../../components/base/Menu.svelte";
  import Editor from "../../components/Editor.svelte";
  import Edit from "../../components/icons/Edit.svelte";
  import Check from "../../components/icons/Check.svelte";
  import showdown from "showdown";

  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let title = "";
  export let value = "";
  let isEdit = false;
  let converter = new showdown.Converter();
  let menus = [{ value: "delete", text: "Delete Note", type: "danger" }];
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

  const handleSelectOption = e => {
    switch (e.detail) {
      case "delete":
        dispatch("delete");
        break;

      default:
        break;
    }
  };
</script>

<div class="mb-5">
  <Card name={title} useAction="true" on:rename on:action={handleEdit}>
    {#if isEdit}
      <Editor {value} on:change={handleChange} />
    {:else}
      <div class="px-2">
        {@html htmlValue}
      </div>
    {/if}

    <div slot="option">
      <Menu values={menus} on:select={handleSelectOption} />
    </div>

    <div slot="action">
      {#if isEdit}
        <Check />
      {:else}
        <Edit />
      {/if}
    </div>
  </Card>
</div>
