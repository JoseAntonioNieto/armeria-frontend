<script>
    export let cliente;
</script>

<p class="card-text">Nombre: <input type="text" bind:value={cliente.nombre}/></p>
<p class="card-text">Apellido 1: <input type="text" bind:value={cliente.apellido1}/></p>
<p class="card-text">Apellido 2: <input type="text" bind:value={cliente.apellido2}/></p>