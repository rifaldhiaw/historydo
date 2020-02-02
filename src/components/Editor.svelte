<script>
  import EasyMDE from "easymde";
  import { onMount, onDestroy } from "svelte";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let value = "";
  let easyMDE;

  onMount(() => {
    easyMDE = new EasyMDE({
      element: document.getElementById("note-mde"),
      initialValue: value
    });
    easyMDE.codemirror.on("change", function() {
      dispatch("change", easyMDE.value());
    });
  });

  onDestroy(() => {
    easyMDE.toTextArea();
    easyMDE = null;
  });
</script>

<textarea class="d-none" id="note-mde" />
