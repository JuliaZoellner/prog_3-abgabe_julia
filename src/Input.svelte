<script>
    import CardWrapper from "./components/CardWrapper.svelte";
    import Booster from "./components/Inputs/Booster.svelte";
    import LengthSlider from "./components/Inputs/LengthSlider.svelte";
    import Rocket from "./components/Rocket.svelte";
    import Height from "./components/Inputs/Height.svelte";
    import PayloadSlider from "./components/Inputs/PayloadSlider.svelte";
    import Navbar from "./components/Navbar.svelte";
</script>

<div class="container">
    <Navbar />
    <div class="wrapperGrid">
        <div class="weight">
            <CardWrapper title="Weight">
                <Height />
            </CardWrapper>
        </div>
        <div class="booster">
            <CardWrapper title="Booster">
                <Booster />
            </CardWrapper>
        </div>
        <div class="lengthPayloadWrapper">
            <div class="length">
                <CardWrapper title="Length">
                    <LengthSlider />
                </CardWrapper>
            </div>
            <div class="payload">
                <CardWrapper title="Payload">
                    <PayloadSlider />
                </CardWrapper>
            </div>
        </div>
    </div>
    <div class="rocket">
        <Rocket />
    </div>
    <a class="button btnFixed" href="#/story">Next</a>
</div>

<style>
    .button.btnFixed {
        position: fixed;
        bottom: 0;
        right: 0;
        margin: 2rem;
    }

    .wrapperGrid {
        display: grid;
        grid-template-columns: 0.5fr 1fr 1fr;
        gap: 1rem;
        width: 100%;
        height: 100%;
        padding-top: 60px;
    }

    .booster,
    .rocket {
        height: 100%;
    }

    .length,
    .payload {
        flex-grow: 1;
    }

    .lengthPayloadWrapper {
        height: 100%;
        display: flex;
        gap: 1rem;
        flex-direction: column;
        justify-content: space-between;
    }

    @media (max-width: 1000px) {
        .wrapperGrid {
            grid-template-columns: 1fr;
            grid-template-rows: auto auto auto auto auto;
            padding-top: 60px;
        }

        .weight,
        .booster,
        .length,
        .payload,
        .rocket {
            grid-column: auto;
            grid-row: auto;
            height: auto;
        }

        .rocket {
            padding-top: 10rem; /* Add some spacing above the rocket for better layout on mobile */
            transform: rotate(90deg) scale(0.7); /* Rotate and scale the rocket */
            transform-origin: center center; /* Rotate around the center */
            width: auto;
            height: auto;
        }
    }

    @media (max-width: 500px) {
        .wrapperGrid {
            grid-template-columns: 1fr;
            grid-template-rows: auto auto auto auto auto;
            padding-top: 60px;
        }

        .weight,
        .booster,
        .length,
        .payload {
            grid-column: auto;
            grid-row: auto;
            height: auto;
        }
    }
</style>
