<script>
    import { height, length } from "../../store";

    const maxHeightPx = 250; // Maximum height in pixels

    // Reactive statement to calculate the constrained height
    $: constrainedHeight = Math.min($height * 12, maxHeightPx);

    // Calculate the viewBox based on constrained dimensions
    $: viewBoxX = 0;
    $: viewBoxY = 0;
    $: viewBoxWidth = 167;
    $: viewBoxHeight = 189;
</script>

<div>
    <svg
        width="fit-content"
        height={constrainedHeight}
        viewBox="0 0 167 189"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
    >
        <path
            d="M1.0332 186.736V2L164 86.2179L1.0332 186.736Z"
            stroke="white"
            stroke-width="2"
        />
    </svg>
</div>

<style>
    .rocketFrontWrapper {
        display: flex;
        justify-content: start;
        align-items: center;
    }
</style>
