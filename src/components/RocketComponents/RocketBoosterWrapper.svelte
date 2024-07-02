<script>
    import { booster } from "../../store";
    import Booster from "../Inputs/Booster.svelte";
    import RocketBooster from "./RocketBooster.svelte";
    let boosterHeight;

    $: boosterHeight = $booster * 10;
</script>

<div class="boosterWrapper">
    {#each Array($booster) as _, i}
        <div class="booster" style="height: {boosterHeight}px;">
            <RocketBooster />
        </div>
    {/each}
</div>

<style>
    .boosterWrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;
        height: 100%;
    }
    .booster {
        width: 50px;
        /* background-color: white; */
        transition: height 0.3s ease;
    }
</style>
