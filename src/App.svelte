<script>
	import TodoInput from "./components/TodoInput.svelte";

	export let name;
	import NavBar from "./components/NavBar.svelte";
	import TodoList from "./components/TodoList.svelte";

	let todos = [
		{ id: 0, checked: false, text: "finish Svelte tutorial" },
		{ id: 1, checked: false, text: "build an app" },
		{ id: 2, checked: false, text: "world domination" },
	];
	let onHandleCheck = (id) => {
		const index = todos.findIndex((todo) => todo.id === id);
		todos[index]["checked"] = !todos[index]["checked"];
	};

	let onHandleRemove = (id) => {
		todos = todos.filter((todo) => todo.id !== id);
	};

	let onHandleModify = (id, text) => {
		const index = todos.findIndex((todo) => todo.id === id);
		todos[index]["text"] = text;
	};

	let todoInput = "";

	let onHandleAdd = () => {
		if(!todoInput){
			return;
		}
		const newTodo = {
			id: ++lastId,
			checked: false,
			text: todoInput,
		};
		todos = [...todos, newTodo];

		todoInput = "";
	};

	let onHandleKeyup = e => {
		todoInput = e.target.value;

		if(e.keyCode === 13) {
			onHandleAdd();
		}
	}

	$: lastId = todos[todos.length - 1]?.id || 0;
</script>

<main>
	<section class="hero is-primary is-fullheight">
		<!--		헤더     -->
		<div class="hero-head">
			<NavBar />
		</div>

		<!--	바디		-->
		<div class="hero-body">
			<div class="container has-text-centered">
				<div class="columns is-desktop">
					<div class="column"></div>
					<div class="column">
						<h1 class="title">TODO List</h1>
						<h2 class="subtitle">Built with Svelte, Bulma</h2>
						<TodoInput {todoInput} {onHandleKeyup} {onHandleAdd} />
						<TodoList {todos} {onHandleCheck} {onHandleRemove} {onHandleModify} />
					</div>
					<div class="column"></div>
				</div>
			</div>
		</div>
	</section>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>