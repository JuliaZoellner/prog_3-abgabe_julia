<script>
    import { payload } from "../../store";
    import { onMount } from "svelte";

    let sliderValue = 0;

    // Ensure the store is initialized with the slider value
    onMount(() => {
        payload.set(sliderValue);
    });

    // Reactive statement to update the length store whenever the slider value changes
    $: payload.set(sliderValue);

    console.log($payload);
</script>

<div class="sliderWrapper">
    <input type="range" id="slider" min="0" max="35" bind:value={sliderValue} />
    <label class="input-label" for="slider">{$payload}</label>
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

    @media (max-width: 1024px) {
        .sliderWrapper {
            padding: 15px;
        }

        input[type="range"] {
            height: 7px;
        }

        input[type="range"]::-webkit-slider-thumb {
            width: 22px;
            height: 22px;
        }

        .input-label {
            font-size: 0.95rem;
        }
    }

    @media (max-width: 768px) {
        .sliderWrapper {
            padding: 10px;
        }

        input[type="range"] {
            height: 6px;
        }

        input[type="range"]::-webkit-slider-thumb {
            width: 20px;
            height: 20px;
        }

        .input-label {
            font-size: 0.9rem;
        }
    }

    @media (max-width: 480px) {
        .sliderWrapper {
            padding: 5px;
        }

        input[type="range"] {
            height: 4px;
        }

        input[type="range"]::-webkit-slider-thumb {
            width: 16px;
            height: 16px;
        }

        .input-label {
            font-size: 0.8rem;
        }
    }
</style>
