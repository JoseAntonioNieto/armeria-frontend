<script>
    export let arma;
</script>

<h5 class="card-title"><input type="text" bind:value={arma.nombre}/></h5>
<p class="card-text">Balas cargador: <input type="number" bind:value={arma.balasCargador}/></p>
<p class="card-text">Tipo de arma: <input type="text" bind:value={arma.tipo}/></p>
<p class="card-text">Cantidad en stock: <input type="number" bind:value={arma.stock}/></p>