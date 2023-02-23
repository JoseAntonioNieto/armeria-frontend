<script>
    import { getContext } from "svelte";
    import {data} from "../../store.js";
    import { onMount} from "svelte";
    import Cliente from "./Cliente.svelte";
    import Botones from "../Botones.svelte";
    import Buscador from "../Buscador.svelte";

    let clienteInsert = {}
    let datosFiltrados = {}
    let busqueda = "";

    const url = getContext("URL");
    async function getClientes() {
        const response = await fetch(url.clientes);
        $data = await response.json();
    }

    onMount(getClientes);

    $: datosFiltrados = $data.filter(cliente => RegExp(busqueda, "i").test(cliente.nombre))
</script>
<p>Buscar: <Buscador bind:busqueda/></p>

<div class="container">
    <div class="row">
        <div class="col bg-danger py-3">
            <h2>Insertar</h2>
            <Cliente bind:cliente={clienteInsert}/>
            <Botones tipo="insertar" documento="{clienteInsert}" url="{url.clientes}"/>
        </div>
    </div>
    <div class="row">
        {#each datosFiltrados as cliente}
                <div class="col-md-4">
                    <div class="card mt-3">
                        <div class="card-body">
                            <Cliente bind:cliente/>
                            <Botones tipo="actualizar" documento="{cliente}" url="{url.clientes}"/>
                            <Botones tipo="eliminar" documento="{cliente}" url="{url.clientes}"/>
                        </div>
                    </div>
                </div>
        {/each}
    </div>
</div>