<script>
    import { length } from "../../store";
    import { onMount } from "svelte";

    let sliderValue = 50;

    // Ensure the store is initialized with the slider value
    onMount(() => {
        length.set(sliderValue);
    });

    // Reactive statement to update the length store whenever the slider value changes
    $: length.set(sliderValue);
</script>

<div class="sliderWrapper">
    <input
        type="range"
        id="slider"
        min="10"
        max="100"
        bind:value={sliderValue}
    />
    <label class="input-label" for="slider">{sliderValue}</label>
</div>

<style>
    .sliderWrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 100%;
        margin: auto;
    }

    input[type="range"] {
        -webkit-appearance: none;
        appearance: none;
        width: 100%;
        height: 8px;
        background: #4c4c4c;
        border-radius: 25rem;
        outline: none;
        transition: all 0.3s;
    }

    input[type="range"]::-webkit-slider-thumb {
        -webkit-appearance: none;
        appearance: none;
        width: 24px;
        height: 24px;
        background: #ffffff;
        cursor: pointer;
        border-radius: 50%;
        border: 1px solid #4c4c4c;
    }

    .input-label {
        position: absolute;
        top: 24px;
        right: 24px;
        opacity: 0.3;
        font-family: "socialmono", monospace;
    }
</style>
