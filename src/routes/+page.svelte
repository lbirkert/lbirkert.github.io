<script>
    import { browser } from "$app/environment";
    import Page from "$lib/Page.svelte";
    import { onMount } from "svelte";

    let mount = false;
    onMount(() => (mount = browser && true));
</script>

<svelte:head>
    <title>Lucas Birkert</title>
</svelte:head>

<hero class:mount>
    <div>
        <h1>Lucas Birkert</h1>

        <p>Web Developement & Design</p>

        <br />

        <p>
            I am a web and software developer focusing on simplicity. I have got
            more than 3 years of experience in the programming field.
        </p>
    </div>
</hero>

<div class="content">
    <svg
        viewBox="5 115 205 46"
        xmlns="http://www.w3.org/2000/svg"
        preserveAspectRatio="xMidYMid meet"
    >
        <path
            style="fill:var(--brand-background-secondary)"
            d="m -1.6702741,163.66963 c 0,0 22.8354941,-31.58985 40.3040271,-35.83995 18.234713,-4.4365 35.818903,14.94595 54.556512,13.90226 21.351405,-1.18928 38.709505,-20.9064 60.023005,-22.64756 19.25633,-1.57311 56.83154,11.38871 56.83154,11.38871 l 0.0349,31.91975 z"
        />
    </svg>

    <div id="projects" />
    <div class="projects">
        <ul>
            <li>
                <Page
                    urls={{
                        small: "screen_gpx_small.png",
                        medium: "screen_gpx_medium.png",
                    }}
                    url="https://gamepowerx.com/"
                />
            </li>

            <li>
                <Page
                    urls={{
                        small: "screen_kotw_small.png",
                        medium: "screen_kotw_medium.png",
                    }}
                    url="https://kotw.dev/#about"
                />
            </li>

            <li>
                <Page
                    urls={{
                        small: "screen_palaten_small.png",
                        medium: "screen_palaten_medium.png",
                    }}
                    url="https://www.palaten.de/"
                />
            </li>
        </ul>
    </div>
</div>

<style>
    @keyframes title {
        to {
            opacity: 1;
            transform: none;
        }
    }

    hero h1,
    hero h1 + p {
        opacity: 0;
        transform: translateY(-6px);
    }

    hero.mount h1,
    hero.mount h1 + p {
        animation: 0.3s title ease forwards;
    }

    hero.mount h1 + p {
        animation-delay: 0.1s;
    }

    @media (prefers-reduced-motion) {
        * {
            animation: none;
        }
    }

    hero {
        padding: 60px 0;
        width: 90%;
        max-width: 600px;
        margin: auto;
        display: flex;
        column-gap: 30px;
        row-gap: 40px;
    }

    .content svg {
        width: 100%;
        transform: translateY(-20vw);
        position: absolute;
    }

    .content {
        display: flex;
        flex-direction: column;
        background-color: var(--brand-background-secondary);
        margin-top: 20vw;
    }

    .projects ul {
        padding: calc(2.5vw + 25px) 15px;
        overflow-x: scroll;
        display: flex;
        flex-wrap: wrap;
        column-gap: 20px;
        row-gap: 20px;
        list-style: none;
        justify-content: center;
    }

    .projects li {
        width: 600px;
    }

    #projects {
        position: absolute;
        transform: translateY(-60px);
    }
</style>
