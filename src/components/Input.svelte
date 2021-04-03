<script>
    import Movie from "./Movie.svelte";

    let value = "";
    let result = [];
    let loading = false;
    const handleInput = (event) => (value = event.target.value);

    $: if (value.length > 2) {
        loading = true;
        fetch(`http://www.omdbapi.com/?s=${value}&apikey=8183bb76`)
            .then((res) => res.json())
            .then((apiResponse) => {
                result = apiResponse.Search || [];
                loading = false;
            });
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

    {#if loading}
        <strong>Cargando...</strong>
    {:else}
        {#each result as { Title, Poster: poster }}
            <Movie {Title} {poster} />
        {:else}
            <strong>No hay resultados</strong>
        {/each}
    {/if}
</div>

<style>
    /* your styles go here */
</style>
