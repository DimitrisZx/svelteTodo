<script>
	import {onMount } from "svelte/internal";
	import { writable, get } from "svelte/store";
import Todo from "./todo.svelte";
	const todosList = writable([]);
	onMount(() => {
		async function fetchData() {
			console.log
			const response = await fetch('https://jsonplaceholder.typicode.com/todos');
			const parsed = await response.json();
			todosList.set(parsed.filter((item, idx) => idx < 10));
		}
		fetchData();
	})
	export let name;
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{#each $todosList as todo}
		<Todo item={todo} todosList={todosList} />
	{/each}
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