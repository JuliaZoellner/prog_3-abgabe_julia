<script>
    import { booster } from "../../store";

    let boosterHeight;

    // Dynamically calculate booster height based on the number of boosters
    $: boosterHeight = 100 / $booster; // Adjust the divisor based on your design
</script>

<div class="boosterWrapper">
    {#each Array($booster) as _, i}
        <div class="booster" style="height: {boosterHeight}px;">
            <svg
                width="100%"
                height="100%"
                viewBox="0 0 242 52"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
            >
                <path
                    d="M76.5801 1H241V51H76.5801L112.381 38.7451H24.5359L76.5801 30.902L1 23.549L76.5801 19.7908L35.8066 8.84314H96.1381L76.5801 1Z"
                    stroke="white"
                    stroke-width="2"
                />
            </svg>
        </div>
    {/each}
</div>

<style>
    .boosterWrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;

        flex-shrink: 1;
    }
    .booster {
        transition: height 0.3s ease;
    }
</style>
