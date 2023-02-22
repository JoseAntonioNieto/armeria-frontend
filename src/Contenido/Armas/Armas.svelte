<script>
import { getContext} from "svelte";
import { data } from "../../store.js";
import { onMount} from "svelte";
import Buscador from "../Buscador.svelte";
import Arma from "./Arma.svelte";
import Botones from "../Botones.svelte";

let armaInsert = {};
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
<p>Buscar: <Buscador bind:busqueda/></p>

<div class="container">
    <div class="row">
        <div class="col bg-danger py-3">
            <h2>Insertar</h2>
            <Arma bind:arma={armaInsert}/>
            <Botones tipo="insertar"/>
        </div>
    </div>
    <div class="row">
        {#each datosFiltrados as arma }
            <div class="col-md-4">
                <div class="card mt-3">
                    <div class="card-body">
                        <Arma bind:arma/>
                        <Botones tipo="actualizar" />
                        <Botones tipo="eliminar" documento="{arma}" url="{URL.armas}"/>
                    </div>
                </div>
            </div>
        {/each}
    </div>
</div>
