<script>
    let value = "";
    let result;
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
    {:else if result?.length > 0}
        <strong>Tenemos {result.length} peliculas</strong>
    {:else}
        <strong>No hay resultados</strong>
    {/if}
</div>

<style>
    /* your styles go here */
</style>
