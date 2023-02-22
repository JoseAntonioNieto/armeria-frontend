<script>
    import { onMount} from "svelte";

    export let tipo;

    export let url;

    export let documento;

    let handler = () => {}

    function insertar() {
        console.log("Insertar");
    }

    function actualizar() {
        console.log("Actualizar");
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