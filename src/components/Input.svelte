<script>
    let value = "";
    let result = [];
    const handleInput = (event) => (value = event.target.value);

    $: if (value.length > 2) {
        fetch(`http://www.omdbapi.com/?s=${value}&apikey=8183bb76`)
            .then((res) => res.json())
            .then((apiResponse) => {
                result = apiResponse.Search;
            });
    }
</script>

<!-- markup (zero or more items) goes here -->
<div class="Input">
    <input type="text" {value} on:input={handleInput} />
</div>

<style>
    /* your styles go here */
</style>
