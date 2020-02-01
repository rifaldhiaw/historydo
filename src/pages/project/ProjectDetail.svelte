<script>
  import Card from "../../components/base/Card.svelte";
  import OptionIcon from "../../components/icons/option.svelte";
  import TodoCard from "../../components/TodoCard.svelte";
  import Editor from "../../components/Editor.svelte";

  function onClickFunc() {
    alert("on click option in project detail");
  }
</script>

<section>
  <div class="flex justify-between items-center mb-5 px-2">
    <h1>Project 1</h1>
    <OptionIcon on:click={onClickFunc} />
  </div>

  <div class="mb-5">
    <Card name="Todo">
      <TodoCard />
      <TodoCard />
      <TodoCard />
    </Card>
  </div>

  <div class="mb-5">
    <Card name="Habit">
      <TodoCard />
      <TodoCard />
    </Card>
  </div>

  <div class="mb-5">
    <Card name="Note">
      <Editor />
    </Card>
  </div>

</section>
