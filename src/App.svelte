<script>
	import Counter from "./components/Counter.svelte";
	import Input from "./components/Input.svelte";
	let commonProps = {
		maxContador: 25,
	};
</script>

<div class="App">
	<!-- <h1>Contadores</h1>
	<div class="contadores">
		<Counter initialState={5} {...commonProps} />
		<Counter initialState={15} {...commonProps} />
		<Counter initialState={30} {...commonProps} />
	</div> -->
	<div class="inputs">
		<Input />
	</div>
</div>

<style>
	/* .contadores {
		display: flex;
	} */
</style>
