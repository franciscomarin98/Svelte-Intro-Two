<script>
    import Movie from "./Movie.svelte";

    let value = "";
    let result = [];

    const handleInput = (event) => (value = event.target.value);

    $: if (value.length > 2) {
        result = fetch(`http://www.omdbapi.com/?s=${value}&apikey=8183bb76`)
            .then((res) => res.json())
            .then((apiResponse) => apiResponse.Search || []);
    }
</script>

<!-- markup (zero or more items) goes here -->
<div class="Input">
    <input
        placeholder="Search movie"
        type="text"
        {value}
        on:input={handleInput}
    />

    {#await result}
        <strong>Cargando...</strong>
    {:then movies}
        {#each movies as { Title, Poster: poster }}
            <Movie {Title} {poster} />
        {:else}
            <strong>No hay resultados</strong>
        {/each}
    {/await}
</div>

<style>
    /* your styles go here */
</style>
