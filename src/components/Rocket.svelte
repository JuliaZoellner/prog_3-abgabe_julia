<script>
    import RocketBoosterWrapper from "./RocketComponents/RocketBoosterWrapper.svelte";
    import RocketMain from "./RocketComponents/RocketMain.svelte";
    import RocketFront from "./RocketComponents/RocketFront.svelte";
    import RocketBooster from "./RocketComponents/RocketBooster.svelte";
</script>

<div class="rocketWrapper">
    <RocketBoosterWrapper />
    <!-- <RocketBooster /> -->
    <RocketMain />
    <RocketFront />
</div>

<style>
    .rocketWrapper {
        display: flex;
        flex-direction: row; /* Ensure components stack vertically */
        justify-content: center;
        align-items: center;
        padding-top: 200px;

        width: 100%;
        height: 100%;
        min-height: 200px;
    }

    .fullHeight {
        height: auto;
        width: 200px;
        min-height: 10px;
        background-color: blue;
    }

    .rocketWrapper {
        display: flex;
        flex-direction: row; /* Ensure components stack vertically */
        justify-content: center;
        align-items: center;

        width: 100%;
        height: 100%;
        min-height: 200px;
    }
</style>
