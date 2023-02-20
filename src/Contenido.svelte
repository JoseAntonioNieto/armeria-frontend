<script>
    import { Route } from "svelte-routing";
    import Inicio from "./Contenido/Inicio.svelte";
    import Clientes from "./Contenido/Clientes/Clientes.svelte";
    import Armas from "./Contenido/Armas/Armas.svelte";
</script>

<main>
    <Route path="/" component="{Inicio}"></Route>
    <Route path="/clientes" component="{Clientes}"></Route>
    <Route path="/armas" component="{Armas}"></Route>
</main>