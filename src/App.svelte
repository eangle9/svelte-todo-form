<script>
  import Tabs from "./shared/Tabs.svelte";
  import Header from "./components/Header.svelte";
  import Footer from "./components/Footer.svelte";
  import TodoForm from "./components/TodoForm.svelte";
  import TodoList from "./components/TodoList.svelte";

  let tabs = ["Todo List", "Todo Form"];
  let activeTab = "Todo List";
  let todos = [
    {
      id: 1,
      question: "svelte or react?",
      answerA: "svelte",
      answerB: "react",
      voteA: 20,
      voteB: 10,
    },
  ];

  const handleTodo = (e) => {
    activeTab = e.detail;
  };
  const handleAddTodo = (e) => {
    let addtodo = e.detail;
    todos = [addtodo, ...todos];
	activeTab = 'Todo List'
  };
  const handleVote = (e) =>{
	let { id, option } = e.detail;
	let copiedTodos = [...todos]
	let updateTodo = copiedTodos.find((todo) => todo.id === id)
	
	if(option === 'a'){
		updateTodo.voteA++;
	}
	if(option === 'b'){
		updateTodo.voteB++;
	}
	todos = copiedTodos;
	
  }
</script>

<Header />
<main>
  <Tabs {activeTab} {tabs} on:todo={handleTodo} />

  {#if activeTab === "Todo List"}
        <TodoList {todos} on:vote={handleVote} />
  {:else if activeTab === "Todo Form"}
    <TodoForm on:addtodo={handleAddTodo} />
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 940px;
    margin: 0 auto;
  }
  /* .todo {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  } */
</style>
