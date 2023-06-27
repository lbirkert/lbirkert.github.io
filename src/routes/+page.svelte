<script lang="ts">
    import { browser } from "$app/environment";
    import Page from "$lib/Page.svelte";
    import { onMount } from "svelte";
    import { tweened } from "svelte/motion";
    import { cubicOut } from "svelte/easing";
    import Fa from "svelte-fa";
    import {
        faDiscord,
        faGithub,
        faGitlab,
    } from "@fortawesome/free-brands-svg-icons";
    import { faEnvelope } from "@fortawesome/free-solid-svg-icons";

    let mount = false;
    onMount(() => (mount = browser && true));

    let path =
        "0,0 22.8354941,-31.58985 40.3040271,-35.83995 18.234713,-4.4365 35.818903,14.94595 54.556512,13.90226 21.351405,-1.18928 38.709505,-20.9064 60.023005,-22.64756 19.25633,-1.57311 56.83154,11.38871 56.83154,11.38871";

    let start = [-1.6702741, 163.66963];

    let points = path.split(" ").map((e) => e.split(",").map(parseFloat));
    let curves = points.reduce(
        (p, v) => (
            p[p.length - 1].length < 3 ? p[p.length - 1].push(v) : p.push([v]),
            p
        ),
        [[]] as number[][][]
    );

    let segments = curves.map((v, i) => {
        const p0 = i === 0 ? start : curves[i - 1][2];
        v[2][0] += p0[0];
        v[2][1] += p0[1];
        const p3 = v[2];
        const p1 = [v[0][0] + p0[0], v[0][1] + p0[1]];
        const p2 = [v[1][0] + p0[0], v[1][1] + p0[1]];

        return [p0, p1, p2, p3];
    }) as [number[], number[], number[], number[]][];

    let lengths: number[] = [];

    segments.forEach(([p0, p1, p2, p3], i) => {
        lengths.push(
            (Math.sqrt(
                Math.pow(p3[0] - p0[0], 2) + Math.pow(p3[1] - p0[1], 2)
            ) +
                Math.sqrt(
                    Math.pow(p0[0] - p1[0], 2) + Math.pow(p0[1] - p1[1], 2)
                ) +
                Math.sqrt(
                    Math.pow(p1[0] - p2[0], 2) + Math.pow(p1[1] - p2[1], 2)
                ) +
                Math.sqrt(
                    Math.pow(p2[0] - p3[0], 2) + Math.pow(p2[1] - p3[1], 2)
                )) /
                2 +
                (lengths[i - 1] || 0)
        );
    });

    let maxLength = lengths[lengths.length - 1];
    lengths = lengths.map((e) => e / maxLength);

    function interpolate(
        p0: number[],
        p1: number[],
        p2: number[],
        p3: number[],
        t: number
    ) {
        const x =
            Math.pow(1 - t, 3) * p0[0] +
            3 * t * Math.pow(1 - t, 2) * p1[0] +
            3 * Math.pow(t, 2) * (1 - t) * p2[0] +
            Math.pow(t, 3) * p3[0];
        const y =
            Math.pow(1 - t, 3) * p0[1] +
            3 * t * Math.pow(1 - t, 2) * p1[1] +
            3 * Math.pow(t, 2) * (1 - t) * p2[1] +
            Math.pow(t, 3) * p3[1];

        return { x, y };
    }

    let scrollY = 0;
    let innerWidth = 0;

    let scroll = tweened(0, { duration: 400, easing: cubicOut });
    $: scroll.set(scrollY / (innerWidth * 0.25 + 300));

    $: circle_r = 1000 / innerWidth;
    $: circles = Math.floor(innerWidth / 100);

    function circle(scroll: number) {
        if (scroll < 0 || scroll > 1) return { x: 0, y: 0 };

        const i = lengths.findIndex((p) => p >= scroll);

        const minscroll = lengths[i - 1] || 0;
        const maxscroll = lengths[i];

        const t = (scroll - minscroll) / (maxscroll - minscroll);

        return interpolate(...segments[i], t);
    }
</script>

<svelte:window bind:scrollY bind:innerWidth />

<svelte:head>
    <title>Lucas Birkert</title>
</svelte:head>

<hero class:mount>
    <div>
        <h1>Lucas Birkert</h1>

        <p>Web Developement & Design</p>
        <br />

        <p class="short">
            Hey, my name is Lucas and I am an experienced software and web
            developer from germany.
        </p>

        <br />

        <ul class="links">
            <li>
                <a href="https://discord.gg/Cq2UpzeTnm" aria-label="Discord">
                    <Fa icon={faDiscord} />
                </a>
            </li>
            <li>
                <a href="https://github.com/lbirkert" aria-label="Github">
                    <Fa icon={faGithub} />
                </a>
            </li>
            <li>
                <a href="https://gitlab.com/lbirkert" aria-label="Gitlab">
                    <Fa icon={faGitlab} />
                </a>
            </li>
            <li>
                <a href="mailto:lucasbirkert@gmail.com" aria-label="Email">
                    <Fa icon={faEnvelope} />
                </a>
            </li>
        </ul>
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

        {#if $scroll <= 1}
            {#each new Array(circles) as _, i}
                {@const c = circle($scroll - i * (1.0 / circles))}
                <circle
                    cx={c.x}
                    cy={c.y - circle_r}
                    r={circle_r}
                    style="fill:var(--brand-accent)"
                />
            {/each}
        {/if}
    </svg>

    <div id="projects" />
    <div class="projects">
        <ul>
            <li>
                <Page preview="gpx" url="https://gamepowerx.com/" />
            </li>

            <li>
                <Page preview="kotw" url="https://kotw.dev/#about" />
            </li>

            <li>
                <Page preview="palaten" url="https://www.palaten.de/" />
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

    .short {
        max-width: 400px;
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

    hero .links {
        list-style: none;
        display: flex;
        column-gap: 20px;
    }

    hero .links a {
        transition: color 0.3s ease;
        font-size: 25px;
    }

    hero .links a:hover {
        color: var(--brand-primary);
    }

    hero {
        padding: 60px 0;
        width: 90%;
        max-width: 750px;
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
        width: 100%;
        max-width: 750px;
    }

    @media (min-width: 1500px) {
        .projects li {
            width: 600px;
        }
    }

    #projects {
        position: absolute;
        transform: translateY(-60px);
    }
</style>
