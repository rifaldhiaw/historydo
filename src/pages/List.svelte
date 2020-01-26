<script>
  import TodoCard from "../components/TodoCard.svelte";
  import ListSwitcher from "../components/ListSwitcher.svelte";
</script>

<style>
  .w-half {
    width: 50%;
  }
</style>

<section class="mb-5">
  <h2>Resource</h2>
  <div class="flex flex-wrap">
    <div class="w-half p-1">
      <div class="py-2 px-2 bg-white w-full">Link 1</div>
    </div>
    <div class="w-half p-1">
      <div class="py-2 px-2 bg-white w-full">Link 1</div>
    </div>
    <div class="w-half p-1">
      <div class="py-2 px-2 bg-white w-full">Link 1</div>
    </div>
    <div class="w-half p-1">
      <div class="py-2 px-2 bg-white w-full">Link 1</div>
    </div>
  </div>
</section>

<section class="mb-5">
  <h2>Todo</h2>
  <TodoCard />
  <TodoCard />
  <TodoCard />
</section>

<section class="mb-5">
  <h2>Inbox</h2>
  <TodoCard />
  <TodoCard />
  <TodoCard />
</section>

<ListSwitcher />
