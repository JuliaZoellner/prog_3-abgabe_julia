<script>
    export let text = "";
    export let ueberschrift = "";
</script>

<div class="story-text">
    <h2>{ueberschrift}</h2>
    <h3>{text}</h3>
</div>

<style>
    h2 {
        color: white;
    }

    .story-text {
        color: white;

        max-width: 50rem;
    }
</style>
