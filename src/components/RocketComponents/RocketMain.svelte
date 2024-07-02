<script>
    import { height, length, payload } from "../../store";

    const maxHeightPx = 250; // Maximum height in pixels
    const maxLengthPx = 800; // Maximum length in pixels

    let payloadArray = [];

    // Reactive statement to create an array based on the payload value
    $: payloadArray = Array($payload).fill(0);

    // Reactive statement to calculate the constrained height and length
    $: constrainedLength = Math.min($length * 12, maxLengthPx);
    $: constrainedHeight = Math.min($height * 12, maxHeightPx);

    // Calculate the stroke width based on the constrained dimensions
    $: strokeWidth = Math.max(constrainedHeight / 60, 1); // Adjust stroke width as needed

    // Calculate the viewBox based on constrained dimensions
    $: viewBoxX = 0;
    $: viewBoxY = 0;
    $: viewBoxWidth = constrainedLength;
    $: viewBoxHeight = constrainedHeight;
</script>

<div class="rocketMain">
    <svg
        class="rocketMainSvg"
        width={constrainedLength}
        height={constrainedHeight}
        viewBox={`${viewBoxX} ${viewBoxY} ${viewBoxWidth} ${viewBoxHeight}`}
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
    >
        <rect
            x="0"
            y="0"
            width={constrainedLength}
            height={constrainedHeight}
            stroke="white"
            stroke-width={strokeWidth}
        />
        {#each payloadArray as _, i}
            <path
                d={`M${i * 10 + 1.96143} 0V${constrainedHeight}`}
                stroke="white"
                stroke-width={strokeWidth}
            />
        {/each}
    </svg>
</div>

<style>
    .rocketMain {
        /* background-color: blue; */
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>
