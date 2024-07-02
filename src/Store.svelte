<script>
    import { onMount } from "svelte";
    import { writable } from "svelte/store";
    import Tile from "./components/Tile.svelte";
    import StoryText from "./components/StoryText.svelte";
    import Navbar from "./components/Navbar.svelte";

    // Initialize a writable store for rocket data
    const rocketDataStore = writable([]);

    onMount(() => {
        const storedData = localStorage.getItem("rocketData");
        if (storedData) {
            const parsedData = JSON.parse(storedData);
            rocketDataStore.set(parsedData);
        }
    });
</script>

<div class="store-page">
    <!-- Navbar hinzufügen -->
    <Navbar />

    <div class="content">
        <div class="header-container">
            <StoryText ueberschrift={"Your Rockets"} />
        </div>

        <div class="wrapperGrid">
            {#if $rocketDataStore.length === 0}
                <h1>No rockets available</h1>
            {:else}
                {#each $rocketDataStore as rocket}
                    <Tile {rocket} />
                {/each}
            {/if}
        </div>
    </div>
</div>

<style>
    .store-page {
        color: white;
        padding: 20px;
        display: flex;
        justify-content: start;
        align-items: flex-start;
        height: 100vh;
    }

    .content {
        width: 100%;
        max-width: 100%;
        margin-top: 60px; /* Space for fixed navbar */
    }

    .header-container {
        padding-bottom: 10px;
        width: 100%;
    }

    .wrapperGrid {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 20px;
        width: 100%;
    }

    @media (max-width: 1024px) {
        .wrapperGrid {
            grid-template-columns: repeat(2, 1fr);
        }
    }

    @media (max-width: 768px) {
        .wrapperGrid {
            grid-template-columns: repeat(1, 1fr);
        }
    }
</style>
