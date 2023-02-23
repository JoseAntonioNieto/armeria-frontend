<script>
    import "bootstrap/dist/css/bootstrap.min.css";
    import "bootstrap/dist/js/bootstrap.min.js";
	import { setContext} from "svelte";
    import { Router} from "svelte-routing";
    import Nav from "./Nav.svelte";
    import Contenido from "./Contenido.svelte";

    const URL = {
        armas: "https://apiarmeria.onrender.com/api/armeria/armas",
        clientes: "https://apiarmeria.onrender.com/api/armeria/clientes"
    }

    setContext("URL", URL);
</script>

<Router>
    <Nav/>
    <Contenido/>
</Router>