<script>
    import { onMount} from "svelte";
    import {data} from "../store.js";

    export let tipo;

    export let url;

    export let documento;

    let handler = () => {}

    function insertar() {
        const opciones = {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify(documento)
        }

        console.log(url)

        fetch(url, opciones).then(data => console.log(data)).catch()
    }

    function actualizar() {
        let opciones = {
            method: "PUT",
            headers: { "Content-Type": "application/json"},
            body: JSON.stringify(documento)
        }

        fetch(`${url}/${documento._id}`, opciones).then(data => console.log(data)).catch();
    }

    function eliminar() {
        let opciones = {
            method: "DELETE",
            headers: { "Content-Type": "application/json" }
        }

        fetch(`${url}/${documento._id}`, opciones).then(data => console.log(data)).catch();
        console.log("Eliminar");
    }

    function onSetup() {
        if (tipo == "insertar") {
            handler = insertar;
        } else if (tipo == "actualizar") {
            handler = actualizar;
        } else if (tipo == "eliminar") {
            handler = eliminar;
        }
    }

    onMount(onSetup);
</script>

<input type="button" value="{tipo.toUpperCase()}" on:click={handler} class="btn btn-primary">