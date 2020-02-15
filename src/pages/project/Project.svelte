<script>
  import ProjectList from "./ProjectList.svelte";
  import ProjectDetail from "./ProjectDetail.svelte";

  export let params;
</script>

{#if params.id}
  <ProjectDetail id={params.id} />
{:else}
  <ProjectList />
{/if}
