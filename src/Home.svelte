<script>
    import RocketWrapper from "./components/RocketWrapper.svelte";
    import StoryText from "./components/StoryText.svelte";
    import Navbar from "./components/Navbar.svelte";
</script>

<div class="wrapper">
    <Navbar />
    <div class="content">
        <div class="text-section">
            <h1>This is no Rocket Science</h1>
            <div class="text-container">
                <StoryText
                    text={"You might think building a rocket is difficult. Think again! This website makes it possible. Create a rocket in the simplest way imaginable and see how a mission could look like."}
                />
            </div>
            <div class="buttonWrapper">
                <a href="#/input" class="button">Los gehts!</a>
            </div>
        </div>
        <div class="rocket-section">
            <!-- Empty section for balancing the layout -->
        </div>
        <div class="svg-overlay">
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
                    stroke-width="0.25"
                />
            </svg>
        </div>
    </div>
</div>

<style>
    .wrapper {
        display: flex;
        flex-direction: column;
        height: 100vh;
        color: white;
    }

    .content {
        display: flex;
        justify-content: space-between;
        align-items: flex-end;
        flex-grow: 1;
        padding: 2rem;
        position: relative;
        overflow: hidden;
    }

    .text-section {
        max-width: 50%;
    }

    .rocket-section {
        max-width: 50%;
        display: flex;
        justify-content: flex-end;
    }

    .svg-overlay {
        position: absolute;
        top: 40%;
        right: -15%; /* This makes the SVG go out of the screen to the right */
        transform: translateY(-50%);
        width: 70%; /* Increased width to ensure part of it goes off-screen */
        height: 90%;
        pointer-events: none; /* So that the SVG does not interfere with button clicks */
    }
    h1 {
        font-size: 2.5rem;
        margin-bottom: 1rem;
    }

    .buttonWrapper {
        display: flex;
        justify-content: flex-end;
        align-items: center;
        position: absolute;
        bottom: 0;
        right: 0;
    }

    @media (max-width: 768px) {
        .content {
            flex-direction: column;
            justify-content: flex-end;
            align-items: start;
            text-align: start;
        }

        .text-section,
        .rocket-section {
            max-width: 100%;
        }

        .buttonWrapper {
            flex-direction: column;
        }

        .button {
            margin-bottom: 0.5rem;
        }

        .svg-overlay {
            display: none;
            position: static;
            transform: none;
            width: 100%;
            height: auto;
            margin-top: 2rem;
        }
    }
</style>
