<script>
    export let rocket;
</script>

<div class="tile">
    <h3>{rocket.rocketname}</h3>
    <img class="rectangle" src={rocket.imageUrl} alt={rocket.title} />
    <p>{rocket.story.substring(0, 100)}...</p>
    <!-- Zeigt den Anfang des generierten Textes -->
</div>

<style>
    .tile {
        background-color: #222;
        color: white;
        padding: 20px;
        border-radius: 8px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        width: 100%;
    }

    .tile h3 {
        margin: 0 0 10px 0;
    }

    .tile p {
        margin: 0 0 20px 0;
        flex-grow: 1;
    }

    .rectangle {
        background-color: grey;
        margin-top: 10px;
        margin-bottom: 20px;
        width: 100%;
        height: 300px;
        border-radius: 8px;
        object-fit: cover;
    }
</style>
