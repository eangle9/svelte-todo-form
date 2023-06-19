<script>
  export let todos = [];
  import TodoDetail from "./TodoDetail.svelte";
</script>

<div class="list">
  {#each todos as todo (todo.id)}
    <TodoDetail {todo} on:vote />
  {/each}
</div>

<style>
    .list{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>
