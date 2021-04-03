<script>
    export let initialState = 0;
    export let maxContador;

    let contador = initialState;

    const handleClick = () => {
        contador++;
    };

    $: isEvenOrOdd = contador % 2 === 0 ? "Is Even" : "Is Odd";
    $: if (contador > maxContador) {
        contador = 10;
    }
</script>

<!-- markup (zero or more items) goes here -->
<div class="Counter">
    <button on:click={handleClick}>
        Contador: {contador}
    </button>
    {isEvenOrOdd}
    <!-- {contador % 2 === 0 ? 'isEven' : 'isOdd'} -->
</div>

<style>
    .Counter {
        margin: 10px;
    }
</style>
