<script>
    import { push } from "svelte-spa-router";

    function navigateToHome() {
        push("/");
    }

    function navigateToStore() {
        push("/store");
    }

    function navigateToInput() {
        push("/input");
    }
</script>

<nav class="navbar">
    <div class="logo" on:click={navigateToHome}>Julias Rocket Lab</div>
    <div class="nav">
        <div on:click={navigateToInput}>Rakete Erstellen</div>
        <div on:click={navigateToStore}>Meine Raketen</div>
    </div>
</nav>

<style>
    .navbar {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        color: white;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem 2rem;
        z-index: 1000;
        cursor: pointer;
    }

    .logo {
        font-size: 1rem;
        font-weight: bold;
        cursor: pointer;
        color: grey;
    }

    .nav {
        display: flex;
        gap: 2rem;
    }

    .nav div {
        cursor: pointer;
        /* padding: 0.5rem 1rem; */
        /* transition:
            background-color 0.3s,
            color 0.3s; */
    }

    .nav div:hover {
        text-decoration: underline;
    }

    .nav .active {
        background-color: #fff;
    }
</style>
