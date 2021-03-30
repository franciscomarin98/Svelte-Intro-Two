<script>
    export let initialState = 0;
    let contador = initialState;

    const handleClick = () => {
        contador++;
    };
</script>

<!-- markup (zero or more items) goes here -->
<div class="Counter">
    <button on:click={handleClick}>
        Contador: {contador}
    </button>
</div>

<style>
    .Counter {
        margin: 10px;
    }
</style>
