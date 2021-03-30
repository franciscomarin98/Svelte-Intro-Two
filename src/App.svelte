<script>
	import Counter from "./components/Counter.svelte";
</script>

<div class="App">
	<h1>Contadores</h1>
	<div class="contadores">
		<Counter initialState={5} />
		<Counter initialState={15} />
		<Counter initialState={30} />
	</div>
</div>

<style>
	.contadores {
		display: flex;
	}
</style>
