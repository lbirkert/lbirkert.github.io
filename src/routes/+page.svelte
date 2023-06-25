<script>
    import Page from "$lib/Page.svelte";
    import { onMount } from "svelte";

    let show = false;
    onMount(() => (show = true));
</script>

<hero>
    <div>
        <h1 class:show>Lucas Birkert</h1>

        <p class:show>Web Developement & Design</p>

        <br />

        <p>I am a web and software developer focusing on simplicity.</p>
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

    <main>
        <h1>Projects</h1>
        <p>Some of the projects I have worked on include</p>

        <br />
        <br />

        <h2>GamePowerX</h2>
        <p>I designed the website for the GamePowerX group</p>

        <br />

        <Page
            urls={{
                small: "screen_gpx_small.png",
                medium: "screen_gpx_medium.png",
            }}
            url="https://gamepowerx.com/"
        />

        <Page
            urls={{
                small: "screen_kotw_small.png",
                medium: "screen_kotw_medium.png",
            }}
            url="https://kotw.dev/#about"
        />

        <br />
    </main>
</div>

<style>
    #projects {
        position: absolute;
        transform: translateY(-30px);
    }

    .show {
        transform: none;
        opacity: 1;
    }

    hero h1 + p,
    hero h1 {
        opacity: 0;
        transform: translateY(-6px);
        transition: 0.3s all ease;
    }

    hero h1 + p {
        transition-delay: 0.1s;
    }

    @media (prefers-reduced-motion) {
        * {
            transition: none;
        }
    }

    hero {
        display: block;
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

    main {
        width: 90%;
        max-width: 600px;
        margin: auto;
        padding-top: 50px;
    }

    main h1,
    h2 {
        color: var(--brand-on-secondary-primary);
    }

    main p {
        color: var(--brand-on-secondary-secondary);
    }

    .content {
        display: flex;
        flex-direction: column;
        background-color: var(--brand-background-secondary);
        margin-top: 20vw;
    }
</style>
