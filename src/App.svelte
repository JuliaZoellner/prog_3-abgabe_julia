<script>
    import Router from "svelte-spa-router";
    import Home from "./Home.svelte";
    import Input from "./Input.svelte";
    import Story from "./Story.svelte";
    import Store from "./Store.svelte";

    const routes = {
        "/": Home,
        "/input": Input,
        "/story": Story,
        "/store": Store,
        
    };
</script>

<Router {routes} />
