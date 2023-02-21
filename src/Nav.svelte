<script>
    import { Link } from "svelte-routing";
</script>

<nav class="navbar navbar-expand-lg bg-body-tertiary bg-success">
    <div class="container-fluid">
        <Link to="/" class="navbar-brand text-light">Armeria</Link>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
                <li class="nav-item">
                    <Link to="/" class="nav-link text-light">Inicio</Link>
                </li>
                <li class="nav-item">
                    <Link to="/clientes" class="nav-link text-light">Clientes</Link>
                </li>
                <li class="nav-item">
                    <Link to="/armas" class="nav-link text-light">Armas</Link>
                </li>
            </ul>
        </div>
    </div>
</nav>
