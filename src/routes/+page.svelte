<script>
    import { onMount } from "svelte";

    let show = false;
    onMount(() => (show = true));
</script>

<hero>
    <div class="avatar">
        <div>
            <h1 class:show>Lucas Birkert</h1>

            <p class:show>Web Developement & Design</p>

            <br />

            <p>I am a web and software developer focusing on simplicity.</p>
        </div>
        <img src="lucas.jpg" alt="Lucas" />
    </div>
</hero>

<main>
    <svg
        viewBox="5 115 205 46"
        xmlns="http://www.w3.org/2000/svg"
        preserveAspectRatio="xMidYMid meet"
    >
        <path
            style="fill:var(--brand-secondary)"
            d="m -1.6702741,163.66963 c 0,0 22.8354941,-31.58985 40.3040271,-35.83995 18.234713,-4.4365 35.818903,14.94595 54.556512,13.90226 21.351405,-1.18928 38.709505,-20.9064 60.023005,-22.64756 19.25633,-1.57311 56.83154,11.38871 56.83154,11.38871 l 0.0349,31.91975 z"
        />
    </svg>

    <div>
        <h1>Projects</h1>
        <p>Some of the projects I have worked on include</p>

        <br />

        <h1>KeloCAM</h1>
        <p>Cura for your CNC</p>
        <br />
        <p>
            KeloCAM focuses on the simple slicing process that Cura provides for
            CNC Routers and Milling machines. It was developed in rust for
            maximum performance.
        </p>
    </div>
</main>

<style>
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
    }

    hero img {
        width: 110px;
        height: 110px;
        border-radius: 20px;
        margin-left: auto;
    }

    .avatar {
        display: flex;
        column-gap: 30px;
    }

    main svg {
        width: 100%;
        transform: translateY(-20vw);
        position: absolute;
    }

    main div {
        width: 90%;
        max-width: 600px;
        margin: auto;
        height: 100vh;
        padding-top: 30px;
    }

    main div h1 {
        color: var(--brand-on-secondary-primary);
    }

    main div p {
        color: var(--brand-on-secondary-secondary);
    }

    main {
        display: flex;
        flex-direction: column;
        background-color: var(--brand-secondary);
        margin-top: 20vw;
    }
</style>
