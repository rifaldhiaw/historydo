<script>
  import Card from "../../components/base/Card.svelte";
  import Menu from "../../components/base/Menu.svelte";
  import OptionIcon from "../../components/icons/option.svelte";
  import TodoCard from "../../components/TodoCard.svelte";
  import Note from "../../components/widgets/Note.svelte";
  import Todo from "../../components/widgets/Todo.svelte";
  import Plus from "../../components/icons/Plus.svelte";

  export let id;
  // TODO: Fetch Project Detail

  let showMenu = false;
  let titleEl;
  let menus = [
    { value: "addTodo", text: "Add Todo", type: "primary" },
    { value: "addNote", text: "Add Note", type: "primary" },
    { value: "", text: "", type: "-" },
    { value: "rename", text: "Rename Project", type: "primary" },
    { value: "delete", text: "Delete Project", type: "danger" }
  ];
  let { widgets, name } = {
    id: 1,
    name: "Project Name X",
    widgets: [
      {
        id: 1,
        type: "todo",
        title: "My Todo",
        data: [
          {
            id: 1,
            value: "My first todo",
            date: new Date("03-02-2020"),
            isFInished: true
          },
          {
            id: 2,
            value: "The next one",
            date: new Date("04-02-2020"),
            isFInished: false
          },
          {
            id: 3,
            value: "The last",
            date: new Date("04-02-2020"),
            isFInished: false
          }
        ]
      },
      {
        id: 2,
        type: "note",
        title: "Note Imp",
        data: "# Its H1 \n * and some bullet \n * this one"
      }
    ]
  };

  const handleSelectMenu = e => {
    let newWidget;
    switch (e.detail) {
      case "addTodo":
        newWidget = {
          id: widgets.length + 1,
          type: "todo",
          title: "New todo",
          data: []
        };
        widgets = [...widgets, newWidget];
        break;
      case "addNote":
        newWidget = {
          id: widgets.length + 1,
          type: "note",
          title: "New Note",
          data: ""
        };
        widgets = [...widgets, newWidget];
        break;
      default:
        break;
    }
  };
  const handleUpdateNote = (id, value) => {
    widgets = widgets.map(wd => {
      if (wd.id === id) {
        wd.data = value;
      }
      return wd;
    });
  };
  const handleRename = (id, value) => {
    widgets = widgets.map(wd => {
      if (wd.id === id) {
        wd.title = value;
      }
      return wd;
    });
  };
  const handleEnterName = e => {
    if (e.key === "Enter") {
      titleEl.blur();
    }
  };
  const handleDeleteWidget = id => {
    widgets = widgets.filter(wd => wd.id !== id);
  };
</script>

<section>
  <div class="flex justify-between items-center mb-5 px-2">
    <h1
      bind:this={titleEl}
      bind:innerHTML={name}
      contenteditable="true"
      on:keypress={handleEnterName}>
      {name}
    </h1>
    <Menu values={menus} on:select={handleSelectMenu} />
  </div>

  {#each widgets as wd}
    {#if wd.type == 'todo'}
      <Todo
        title={wd.title}
        todos={wd.data}
        on:delete={() => handleDeleteWidget(wd.id)}
        on:rename={e => handleRename(wd.id, e.detail)} />
    {:else if wd.type == 'note'}
      <Note
        title={wd.title}
        on:change={e => handleUpdateNote(wd.id, e.detail)}
        on:delete={() => handleDeleteWidget(wd.id)}
        on:rename={e => handleRename(wd.id, e.detail)}
        value={wd.data} />
    {:else}
      <div />
    {/if}
  {/each}

</section>
