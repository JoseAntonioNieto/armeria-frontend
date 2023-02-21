<script>
import { getContext} from "svelte";
import { data } from "../../store.js";
import { onMount} from "svelte";
import Buscador from "../Buscador.svelte";



let datosFiltrados = {}
let busqueda = "";
const URL = getContext("URL");

async function getArmas() {
    const response = await fetch(URL.armas);
    $data = await response.json();
}
onMount(getArmas);

$: datosFiltrados = $data.filter( arma => RegExp(busqueda, "i").test(arma.nombre));
</script>
<Buscador bind:busqueda/>

<div class="container">
    <div class="row">
        {#each datosFiltrados as arma }
            <div class="col-md-4">
                <div class="card mt-3">
                    <div class="card-body">
                        <h5 class="card-title">{arma.nombre}</h5>
                        <p class="card-text">Balas cargador: {arma.balasCargador}</p>
                        <p class="card-text">Tipo de arma: {arma.tipo}</p>
                        <p class="card-text">Cantidad en stock: {arma.stock}</p>
                        <a href="#" class="btn btn-primary">Go somewhere</a>
                    </div>
                </div>
            </div>
        {/each}
    </div>
</div>
