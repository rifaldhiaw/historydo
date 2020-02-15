<script>
  import Card from "../base/Card.svelte";
  import Checklist from "../base/Checklist.svelte";

  export let todos = [];

  const handleClick = () => alert("on click option in project detail");
</script>

<div class="mb-5">
  <Card name="Todo" useOption="true" on:optionClick={handleClick}>
    {#each todos as todo, i (todo.id)}
      <Checklist isFinished={todo.isFinished} value={todo.value} />
    {/each}
  </Card>
</div>
