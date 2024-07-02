<script>
    import { onMount } from "svelte";
    import Rocket from "./components/Rocket.svelte";
    import StoryText from "./components/StoryText.svelte";
    import Navbar from "./components/Navbar.svelte";
    import OpenAI from "openai";
    import { length, height, payload, booster } from "./store";
    import RocketNames from "./components/RocketNames.svelte";

    let isLoading = false;
    let name = "";
    let isGenatingImage = false;
    let imageUrl = "";
    let responseText = "";

    const rocketImageSrc =
        "/mnt/data/Bildschirmfoto 2024-06-30 um 14.50.19.png"; // Update this path as needed

    const runPromptForName = async () => {
        const config = {
            apiKey: import.meta.env.VITE_OPENAI_API_KEY,
            dangerouslyAllowBrowser: true,
        };

        const openai = new OpenAI(config);

        try {
            const prompt = `Erfinde einen einzigartigen und kreativen Namen für eine Rakete. Nur  bis zu 4 Wörter. In Englisch. Die Rakete hat folgende Eigenschaften:
            Länge: ${$length}
            Höhe: ${$height}
            Booster: ${$booster}
            Nutzlast: ${$payload}`;

            const response = await openai.chat.completions.create({
                model: "gpt-3.5-turbo",
                messages: [{ role: "user", content: prompt }],
            });

            console.log("API-Response for Name:", response);
            name = response.choices[0].message.content.trim();
            console.log("Rocket Name:", name);
        } catch (error) {
            console.error("Error while retrieving the rocket name:", error);
            name = "Unbekannte Rakete";
        }
    };

    const runPromptForStory = async () => {
        const config = {
            apiKey: import.meta.env.VITE_OPENAI_API_KEY,
            dangerouslyAllowBrowser: true,
        };

        const openai = new OpenAI(config);

        try {
            isLoading = true;

            const prompt = `Erzähle eine Geschichte zu einer Rakete mit folgenden Daten:
            Länge: ${$length}
            Höhe: ${$height}
            Booster: ${$booster}
            Nutzlast: ${$payload}
            Die Geschichte sollte etwa 500 Zeichen lang sein. Erzähle auf eine lustige Art und Weise, wie weit die Rakete fliegen würde. In Englisch`;

            const response = await openai.chat.completions.create({
                model: "gpt-3.5-turbo",
                messages: [{ role: "user", content: prompt }],
            });

            console.log("API-Response for Story:", response);
            responseText = response.choices[0].message.content.trim();
        } catch (error) {
            console.error("Error while retrieving the story:", error);
            responseText = "Fehler beim Abrufen der Geschichte.";
        } finally {
            isLoading = false;
        }
    };

    const generateImage = async () => {
        const config = {
            apiKey: import.meta.env.VITE_OPENAI_API_KEY,
            dangerouslyAllowBrowser: true,
        };

        const openai = new OpenAI(config);

        try {
            isGenatingImage = true;

            const prompt = `The image should show a more realistic picture of a rocket with the following specifications:
            Länge: ${$length}
            Höhe: ${$height}
            Booster: ${$booster}
            Nutzlast: ${$payload}. 
           Plane colorfull background, blue or green. only one color.
Ensure the overall aesthetic has a retro, 80s-inspired vibe with a modern twist. Show only One rocket and teh clean background. No other informations.
            `;

            const response = await openai.images.generate({
                model: "dall-e-3",
                prompt: prompt,
                size: "1024x1792",
                quality: "standard",
            });

            console.log("API-Response for Image:", response);
            imageUrl = response.data[0].url;
        } catch (error) {
            console.error("Error while generating the image:", error);
        } finally {
            isGenatingImage = false;
        }
    };

    onMount(async () => {
        await runPromptForName();
        await runPromptForStory();
        await generateImage();
    });

    const buttonHandler = async () => {
        // Retrieve the existing rocket data from localStorage
        const storedData = localStorage.getItem("rocketData");
        let rocketData = storedData ? JSON.parse(storedData) : [];

        // Add the new rocket data to the array
        rocketData.push({ rocketname: name, story: responseText, imageUrl });

        // Store the updated array back in localStorage
        localStorage.setItem("rocketData", JSON.stringify(rocketData));

        // Route to /store
        window.location.href = "#/store";
    };
</script>

<Navbar />

<div class="story-page">
    {#if isLoading}
        <div class="loading">Loading...</div>
    {:else}
        <div class="image-container">
            {#if imageUrl}
                <img
                    class="generatedImage"
                    src={imageUrl}
                    alt="Generated Rocket"
                />
            {:else}
                <div class="loading">Generating Image...</div>
            {/if}
        </div>

        <div class="text-container">
            <RocketNames rocketname={name} />
            <StoryText text={responseText} />
        </div>
        <div class="button-container">
            <button
                class="button btnFixed"
                on:click={async () => await buttonHandler()}>Next</button
            >
        </div>
    {/if}
</div>

<style>
    .story-page {
        display: grid;
        grid-template-columns: 1fr 1fr;
        color: white;
        height: 100vh;
        padding: 20px;
        position: relative;
        padding-top: 80px; /* Space for fixed navbar */
    }

    .image-container {
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #333;
        padding: 20px;
        height: 100%; /* Ensure the image container takes full height */
    }

    .generatedImage {
        width: 100%;
        height: auto;
        max-height: 90vh;
        object-fit: cover;
    }

    .text-container {
        padding-bottom: 20px;
        padding-left: 20px;
        padding-right: 20px;
        display: flex;
        flex-direction: column;
        gap: 20px;
    }

    .button-container {
        position: absolute;
        bottom: 20px;
        right: 20px;
        display: flex;
        align-items: center;
        gap: 10px;
    }

    .button.btnFixed {
        background-color: white;
        color: black;
        border: none;
        padding: 10px 20px;
        cursor: pointer;
        text-decoration: none;
    }

    .loading {
        color: white;
        font-size: 1.5rem;
    }

    @media (max-width: 768px) {
        .story-page {
            grid-template-columns: 1fr;
            grid-template-rows: auto auto auto;
            gap: 20px;
            height: auto; /* Adjust height for mobile */
            padding-top: 60px; /* Space for fixed navbar */
        }

        .image-container {
            height: auto; /* Adjust height for mobile */
            padding: 10px;
        }

        .generatedImage {
            max-height: 50vh; /* Limit image height on mobile */
        }

        .text-container {
            padding: 10px;
        }
    }
</style>
