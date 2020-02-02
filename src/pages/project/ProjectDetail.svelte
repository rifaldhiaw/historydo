<script>
  import Card from "../../components/base/Card.svelte";
  import OptionIcon from "../../components/icons/option.svelte";
  import TodoCard from "../../components/TodoCard.svelte";
  import Note from "../../components/widgets/Note.svelte";

  let noteValue;

  // Dummy
  let note = `# Its H1
  * and some bullet
  * this one too
  `;

  const handleClick = () => alert("on click option in project detail");
  const handleNote = e => (noteValue = e.detail);
</script>

<section>
  <div class="flex justify-between items-center mb-5 px-2">
    <h1>Project 1</h1>
  </div>

  <div class="mb-5">
    <Card name="Todo" useOption="true" on:optionClick={handleClick}>
      <TodoCard />
      <TodoCard />
      <TodoCard />
    </Card>
  </div>

  <div class="mb-5">
    <Card name="Habit" useOption="true" on:optionClick={handleClick}>
      <TodoCard />
      <TodoCard />
    </Card>
  </div>

  <Note on:change={handleNote} value={note} />

</section>
