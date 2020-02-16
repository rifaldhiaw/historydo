<script>
  import Card from "../base/Card.svelte";
  import Menu from "../base/Menu.svelte";
  import Checklist from "../base/Checklist.svelte";
  import Check from "../../components/icons/Check.svelte";
  import Plus from "../icons/Plus.svelte";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let todos = [];
  export let title = "";
  let value;
  let isAdd = false;
  let menus = [{ value: "delete", text: "Delete Todo", type: "danger" }];

  const handleAdd = () => {
    if (isAdd && value) {
      addNewValue();
    }
    isAdd = !isAdd;
  };

  const handleKeyupAdd = e => {
    if (e.key == "Enter") {
      addNewValue();
    }
  };

  const addNewValue = () => {
    if (value) {
      const newTodo = {
        id: todos.length + 1,
        value: value,
        date: new Date(),
        isFInished: false
      };
      todos = [...todos, newTodo];
      value = "";
    }
  };

  const handleEdited = (id, value) => {
    if (value) {
      todos = todos.map(todo => {
        if (todo.id == id) {
          todo.value = value;
        }

        return todo;
      });
    } else {
      console.log(id);
      todos = todos.filter(todo => todo.id !== id);
    }
  };

  const handleRemove = id => {
    console.log(id);
    todos = todos.filter(todo => todo.id !== id);
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
  <Card name={title} on:rename useAction="true" on:action={handleAdd}>
    {#each todos as todo, i (todo.id)}
      <Checklist
        on:edited={e => handleEdited(todo.id, e.detail)}
        on:remove={() => handleRemove(todo.id)}
        isFinished={todo.isFinished}
        value={todo.value} />
    {/each}

    {#if isAdd}
      <div class="mx-3 mt-5">
        <!-- svelte-ignore a11y-autofocus -->
        <input
          class="appearance-none border-2 rounded w-full py-2 px-3 leading-tight
          focus:outline-none"
          id="todo"
          bind:value
          autofocus
          on:keyup={handleKeyupAdd}
          type="text"
          placeholder="type here, use enter to keep entry ..." />
      </div>
    {/if}

    <div slot="option">
      <Menu values={menus} on:select={handleSelectOption} />
    </div>

    <div slot="action">
      {#if isAdd}
        <Check />
      {:else}
        <Plus />
      {/if}
    </div>
  </Card>
</div>
