<script lang="ts">
  import { browser } from "$app/environment";
  import mobile from "is-mobile";

  export let preview: string = "gpx";
  export let url: string = "https://gamepowerx.com";
</script>

<page>
  <header>
    <a class="url" href={url}>{url}</a>
  </header>

  <img
    src="screen_{preview}_{browser && mobile() ? 'mobile' : 'desktop'}.webp"
    alt="Preview for {preview}"
  />
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
  }

  header {
    background-color: var(--brand-background-secondary);
    border-radius: 10px 10px 0 0;
    padding: 10px 20px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  header .url {
    display: block;
    color: var(--brand-secondary);
    cursor: pointer;
    text-decoration: none;
    background-color: var(--brand-background);
    padding: 5px 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: auto;
  }

  header .url:hover {
    text-decoration: underline;
    color: var(--brand-primary);
  }
</style>
