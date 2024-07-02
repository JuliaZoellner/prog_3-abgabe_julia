<script>
    export let title = "Card Title";
    export let description = "";
</script>

<div class="cardWrapper">
    <div class="cardHeaderWrapper">
        <h3>{title}</h3>
        {#if description}
            <p class="text-small">{description}</p>
        {/if}
    </div>
    <slot />
</div>

<style>
    .cardWrapper {
        background-color: #212121;
        border-radius: 18px;
        padding: 1.5rem;
        margin: 0;
        height: 100%;
        display: flex;
        flex-direction: column;

        align-items: start;
        justify-content: strt;
        min-height: 80px;
        position: relative;
    }

    .cardHeaderWrapper {
        height: 100%;
        display: flex;
        margin-bottom: 0.5rem;
        flex-direction: column;
        text-align: start;
        gap: 0.25rem;
    }
</style>
