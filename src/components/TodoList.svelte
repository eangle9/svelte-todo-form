<script>
  export let todo = [];
  import TodoDetail from "./TodoDetail.svelte";
</script>

<div class="list">
  <TodoDetail {todo} on:vote />
</div>

<style>
</style>
