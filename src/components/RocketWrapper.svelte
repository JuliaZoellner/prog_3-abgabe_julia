<script>
</script>

<div class="">
    <svg
        class="rocket"
        viewBox="0 0 1000 200"
        xmlns="http://www.w3.org/2000/svg"
    >
        <!-- Rocket booster -->
        <rect x="0" y="50" width="150" height="30" stroke="#fff" fill="none" />
        <rect x="0" y="90" width="150" height="30" stroke="#fff" fill="none" />
        <rect x="0" y="130" width="150" height="30" stroke="#fff" fill="none" />

        <!-- Flames -->
        <polygon points="0,50 30,70 0,90" stroke="#fff" fill="none" />
        <polygon points="0,90 30,110 0,130" stroke="#fff" fill="none" />
        <polygon points="0,130 30,150 0,170" stroke="#fff" fill="none" />

        <!-- Main body -->
        <rect
            x="150"
            y="50"
            width="600"
            height="110"
            stroke="#fff"
            fill="none"
        />

        <!-- Sections -->
        {#each Array(20).fill(0) as _, i}
            <line
                x1={180 + i * 30}
                y1="50"
                x2={180 + i * 30}
                y2="160"
                stroke="#fff"
            />
        {/each}

        <!-- Nose cone -->
        <polygon points="750,50 850,105 750,160" stroke="#fff" fill="none" />
    </svg>
</div>

<style>
    .rocketContainer {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 200px;
        margin-top: 2rem;
    }

    .rocket {
        width: 100%;
        max-width: 800px;
    }
</style>
