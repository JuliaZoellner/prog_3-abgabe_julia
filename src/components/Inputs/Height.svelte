<script>
    // Array to hold the state of each rectangle (selected or not)
    import { height } from "../../store";

    // Initialize the array with the first 20 elements set to true
    let selectedRects = Array(35)
        .fill(false)
        .map((_, i) => i < 20);

    // Set the initial height value in the store
    height.set(20);

    // Function to handle rectangle click
    function toggleRect(index) {
        selectedRects = selectedRects.map((_, i) => i <= index);
        height.set(index + 1);
        console.log($height);
    }
</script>

<div class="weightWrapperGrid">
    {#each selectedRects as selected, index}
        <div
            class="rect {selected ? 'selected' : ''}"
            on:click={() => toggleRect(index)}
        ></div>
    {/each}
</div>

<style>
    .weightWrapperGrid {
        display: grid;
        grid-template-columns: repeat(12, 1fr);
        gap: 1rem;
        margin: auto;
    }
    .rect {
        width: 25px;
        height: 25px;
        border: 2px solid #fff;
        cursor: pointer;
        transition: background-color 0.3s;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .selected {
        background-color: #fff;
        color: #000;
    }

    @media (max-width: 768px) {
        .weightWrapperGrid {
            grid-template-columns: repeat(4, 1fr);
        }

        .rect {
            width: 20px;
            height: 20px;
        }
    }

    @media (max-width: 480px) {
        .weightWrapperGrid {
            grid-template-columns: repeat(3, 1fr);
        }

        .rect {
            width: 15px;
            height: 15px;
        }
    }
</style>
