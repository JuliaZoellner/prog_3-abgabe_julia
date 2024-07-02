<script>
    let selectedTab = "neueRocket";

    function selectTab(tab) {
        selectedTab = tab;
    }
</script>

<header class="header">
    <div class="logo">
        <img src="path/to/your/logo.png" alt="Logo" />
    </div>
    <nav class="nav">
        <div
            class:active={selectedTab === "neueRocket"}
            on:click={() => selectTab("neueRocket")}
        >
            Neue Rocket
        </div>
        <div
            class:active={selectedTab === "meineRockets"}
            on:click={() => selectTab("meineRockets")}
        >
            Meine Rockets
        </div>
    </nav>
</header>

<style>
    .header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem 2rem;
        background-color: #333;
        color: white;
    }

    .logo img {
        height: 50px; /* Adjust the height of the logo as needed */
    }

    .nav {
        display: flex;
        gap: 2rem;
    }

    .nav div {
        cursor: pointer;
        padding: 0.5rem 1rem;
        transition:
            background-color 0.3s,
            color 0.3s;
    }

    .nav div:hover {
        background-color: #555;
    }

    .nav .active {
        background-color: #fff;
        color: #333;
    }
</style>
