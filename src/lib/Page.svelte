<script lang="ts">
  import Fa from "svelte-fa";
  import { faArrowUpRightFromSquare } from "@fortawesome/free-solid-svg-icons";

  import { onMount } from "svelte";

  export let preview: string = "gpx";
  export let url: string = "https://gamepowerx.com";

  let mount = false;
  onMount(() => (mount = true));
</script>

<page class:mount>
  <header>
    <a class="url" href={url}>
      {url}
      <Fa icon={faArrowUpRightFromSquare} />
    </a>
  </header>

  <picture>
    <source
      media="(min-resolution: 2x)"
      srcset="screen_{preview}_desktop_3x.webp"
    />
    <source
      media="(min-resolution: 1x)"
      srcset="screen_{preview}_desktop_2x.webp"
    />
    <img src="screen_{preview}_desktop_1x.webp" alt="Preview for {preview}" />
  </picture>
</page>

<style>
  page {
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    box-shadow: 0px 0px 30px 10px rgba(0, 0, 0, 0.3);
    border: 1px solid rgba(255, 255, 255, 0.1);
  }

  img {
    width: 100%;
    pointer-events: none;
    border-radius: 0 0 10px 10px;
    aspect-ratio: 800 / 650;
    opacity: 0;
  }

  page.mount img {
    animation: fadein 0.3s ease forwards;
  }

  @keyframes fadein {
    to {
      opacity: 1;
    }
  }

  header {
    position: relative;
    background-color: var(--brand-background-secondary);
    border-radius: 10px 10px 0 0;
    padding: 10px 20px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  header .url {
    display: flex;
    justify-content: space-between;
    color: var(--brand-secondary);
    cursor: pointer;
    text-decoration: none;
    background-color: var(--brand-background);
    padding: 5px 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: auto;
    transition: color 0.3s ease;
  }

  header .url:hover {
    text-decoration: underline;
    color: var(--brand-primary);
  }

  header::after {
    content: "";
    display: block;
    position: absolute;
    left: 0;
    bottom: 0;
    height: 2px;
    width: 0%;
    background-color: var(--brand-accent);
    animation: loading-bar 0.6s ease forwards;
  }

  @keyframes loading-bar {
    to {
      width: 100%;
    }
  }

  page.mount header::after {
    display: none;
  }
</style>
