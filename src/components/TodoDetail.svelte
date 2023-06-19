<script>
  import Card from "../shared/Card.svelte";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let todo;
  $: totalvalue = todo.voteA + todo.voteB;
  const handleClick = (id, option) => {
    dispatch("vote", { id, option });
  };
</script>

<Card>
  <div class="todo-detail">
    <h3>{todo.question}</h3>
    <p>Total Value : {totalvalue}</p>
    <div class="answer" on:click={() => handleClick(todo.id, 'a')}>
      <div class="payment payment-a" />
      <span>Answer A {todo.answerA}({todo.voteA})</span>
    </div>
    <div class="answer" on:click={() => handleClick(todo.id, 'b')}>
      <div class="payment payment-b" />
      <span>Answer B {todo.answerB}({todo.voteB})</span>
    </div>
  </div>
</Card>

<style>
  h3 {
    margin: 0;
    color: #555;
    font-size: 18px;
    font-weight: bold;
  }
  p {
    margin: 6px 0px 30px;
    font-size: 12px;
    color: #666;
  }
  .answer {
    padding: 10px 0px;
    background-color: #f7f7f7;
    margin: 10px 0;
    cursor: pointer;
  }
  span {
    margin: 0 14px;
    font-size: 14px;
  }
</style>
