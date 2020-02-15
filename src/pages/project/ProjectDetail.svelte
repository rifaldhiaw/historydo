<script>
  import Card from "../../components/base/Card.svelte";
  import OptionIcon from "../../components/icons/option.svelte";
  import TodoCard from "../../components/TodoCard.svelte";
  import Note from "../../components/widgets/Note.svelte";
  import Todo from "../../components/widgets/Todo.svelte";

  export let id;

  // TODO: Fetch Project Detail

  let { widgets, name } = {
    id: 1,
    name: "Project Name X",
    widgets: [
      {
        id: 1,
        type: "todo",
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
        data: "# Its H1 \n * and some bullet \n * this one"
      }
    ]
  };

  const handleClick = () => alert("on click option in project detail");
  const handleNote = (id, value) => {
    console.log("trig");
    widgets = widgets.map(wd => {
      if (wd.id == id) {
        wd.data = value;
      }
      return wd;
    });
  };
</script>

<section>
  <div class="flex justify-between items-center mb-5 px-2">
    <h1>{name}</h1>
  </div>

  {#each widgets as wd}
    {#if wd.type == 'todo'}
      <Todo todos={wd.data} />
    {:else if wd.type == 'note'}
      <Note on:change={e => handleNote(wd.id, e.detail)} value={wd.data} />
    {:else}
      <div />
    {/if}
  {/each}

</section>
