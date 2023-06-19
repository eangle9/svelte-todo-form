<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  import Button from "../shared/Button.svelte";
  let fields = { question: "", answerA: "", answerB: "" };
  let errors = { question: "", answerA: "", answerB: "" };
  let valid = false;
  const handleSubmit = () => {
    valid = true;
    if (fields.question.trim().length < 5) {
      valid = false;
      errors.question = "Question at least 6 length of character long ";
    } else {
      errors.question = "";
    }
    if (fields.answerA.trim().length < 1) {
      valid = false;
      errors.answerA = "answer A is required";
    } else {
      errors.answerA = "";
    }
    if (fields.answerB.trim().length < 1) {
      valid = false;
      errors.answerB = "answer B is required";
    } else {
      errors.answerB = "";
    }
    if (valid) {
      let list = { ...fields, voteA: 0, voteB: 0, id: Math.random() };
      dispatch("addtodo", list);
    }
  };
</script>

<div class="todo-form">
  <form on:submit|preventDefault={handleSubmit}>
    <div class="text-field">
      <label for="question">Question:</label>
      <input type="text" id="question" bind:value={fields.question} />
      <div class="errors">{errors.question}</div>
    </div>
    <div class="text-field">
      <label for="AnswerA:">Answer A:</label>
      <input type="text" id="AnswerA" bind:value={fields.answerA} />
      <div class="errors">{errors.answerA}</div>
    </div>
    <div class="text-field">
      <label for="AnswerB">Answer B:</label>
      <input type="text" id="AnswerB" bind:value={fields.answerB} />
      <div class="errors">{errors.answerB}</div>
    </div>
    <Button>Add todo</Button>
  </form>
</div>

<style>
  .todo-form {
    width: 400px;
    margin: 0 auto;
  }
  form {
    text-align: center;
    /* width: 400px;
    margin: 0 auto; */
  }
  .text-field {
    margin: 18px auto;
  }
  input {
    width: 100%;
    /* box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.2); */
    /* padding: 8px 12px; */
    border-radius: 6px;
  }
  label {
    margin: 10px auto;
    text-align: left;
  }
  .errors {
    font-weight: bold;
    font-size: 12px;
    color: #d91b42;
  }
</style>
