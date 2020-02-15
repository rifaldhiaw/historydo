<script>
  export let isFinished;
  export let value;
</script>

<div class="px-5 py-2 w-full flex items-center text-gray-700">
  <input type="checkbox" name={value} bind:checked={isFinished} class="mr-2" />
  <div>{value}</div>
</div>
