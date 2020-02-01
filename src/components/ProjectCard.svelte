<script>
  import Card from "./base/Card.svelte";

  import ProjectCardBadge from "./ProjectCardBadge.svelte";
  import Icon from "fa-svelte";
  import { faEllipsisV } from "@fortawesome/free-solid-svg-icons/faEllipsisV";

  export let name;
</script>

<a href="/project/123">
  <Card {name}>
    <div class="flex flex-wrap">
      <ProjectCardBadge value="Todo" />
      <ProjectCardBadge value="Habit" />
      <ProjectCardBadge value="Note 1" />
      <ProjectCardBadge value="Note 2 Example" />
    </div>
  </Card>
</a>
