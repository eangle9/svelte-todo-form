<script>
  import Card from "../shared/Card.svelte";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let todo;
  $: totalvalue = todo.voteA + todo.voteB;
  console.log(totalvalue)
  $: percentA = Math.floor(100/totalvalue*todo.voteA)
  $: percentB = Math.floor(100/totalvalue * todo.voteB)
  const handleClick = (id, option) => {
    dispatch("vote", { id, option });
  };
</script> 

<Card>
  <div class="todo-detail">
    <h3>{todo.question}</h3>
    <p>Total Value : {totalvalue}</p>
    <div class="answer" on:click={() => handleClick(todo.id, "a")}>
      <div class="payment payment-a" style="width:{percentA}%"/>
      <span>Answer A {todo.answerA}({todo.voteA})</span>
    </div>
    <div class="answer" on:click={() => handleClick(todo.id, "b")}>
      <div class="payment payment-b" style="width: {percentB}%"></div>
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
    background-color: #f7f7f7;
    margin: 10px 0;
    cursor: pointer;
    position: relative;
  }
  .answer:hover{
    opacity: 0.7;
  }
  span {
    font-size: 14px;
    display: inline-block;
    padding: 10px 20px;
  }
  .payment {
    position: absolute;
    height: 100%;
    box-sizing: border-box;
  }
  .payment-a{
    background-color: rgba(217, 27, 66, 0.2);
    border-left: 4px solid #d91b42;
  }
  .payment-b{
    background-color: rgba(69, 196, 150, 0.2);
    border-left: 4px solid #45c496;
  }
</style>
