<script>
  import TodoCard from "../components/TodoCard.svelte";
  import ListSwitcher from "../components/ListSwitcher.svelte";
  import ProjectCard from "../components/ProjectCard.svelte";
  import Card from "../components/base/Card.svelte";
  import OptionIcon from "../components/icons/option.svelte";

  function onClickFunc() {
    alert("on click option in project detail");
  }
</script>

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
    <div class="p-2 pb-5">
      <h2>It is my note here</h2>
      <p>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Repudiandae
        aut libero placeat explicabo odio ut beatae, dolore ex aliquam vitae,
        necessitatibus minima non quis doloribus optio ipsum dicta veniam dolor.
      </p>

      <br />
      <br />
      <ul>
        <li>hello 1</li>
        <li>hello 2</li>
        <li>hemm is it?</li>
      </ul>
    </div>
  </Card>
</div>
