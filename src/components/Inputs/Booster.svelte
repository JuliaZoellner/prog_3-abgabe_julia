<script>
    import { booster } from "../../store";
    let selectedButton = 2;

    let selectionValues = [1, 2, 3, 4, 5];
    $: booster.set(selectedButton);
</script>

<div class="buttonGrid">
    {#each selectionValues as buttonNumber}
        <div class="radioButtonWrapper">
            <input
                type="radio"
                id="button{buttonNumber}"
                name="buttons"
                bind:group={selectedButton}
                value={buttonNumber}
            />
            <label class="radioButtonLabel" for="button{buttonNumber}">
                {buttonNumber}
            </label>
        </div>
    {/each}
</div>

<style>
    .buttonGrid {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 1rem;
        margin: auto;
        padding-top: 50px;
    }

    .radioButtonWrapper {
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
    }

    .radioButtonWrapper input[type="radio"] {
        position: absolute;
        opacity: 0;
        cursor: pointer;
        width: 100%;
        height: 100%;
    }

    .radioButtonLabel {
        display: flex;
        justify-content: center;
        align-items: center;
        min-width: 100px;
        padding: 0.75rem;
        background-color: #4c4c4c;
        border-radius: 25rem;
        width: fit-content;
        color: #fff;
        font-size: 1rem;
        font-weight: bold;
        transition:
            background-color 0.3s,
            color 0.3s;
    }

    .radioButtonWrapper input[type="radio"]:checked + .radioButtonLabel {
        background-color: #ffffff;
        color: #000;
    }

    @media (max-width: 1024px) {
        .buttonGrid {
            grid-template-columns: 1fr;
        }
    }

    @media (max-width: 768px) {
        .radioButtonLabel {
            font-size: 0.9rem;
            padding: 0.5rem;
        }
    }

    @media (max-width: 480px) {
        .radioButtonLabel {
            font-size: 0.8rem;
            padding: 0.4rem;
        }
    }
</style>
