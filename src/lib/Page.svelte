<script lang="ts">
  export let urls: { small?: string; medium?: string; large?: string } = {
    small: "screen_gpx_small.png",
    medium: "screen_gpx_medium.png",
    large: "screen_gpx_large.png",
  };

  export let alt: string = "GamePowerX";

  export let url: string = "https://gamepowerx.com";
</script>

<page>
  <header>
    <p class="url">{url}</p>
  </header>

  <main>
    <img
      src={urls.small || urls.medium || urls.large}
      srcset="
      {urls.small ? urls.small + ' 375w,' : ''}
      {urls.medium ? urls.medium + ' 960w,' : ''}
      {urls.large ? urls.large + ' 1920w,' : ''}
      "
      sizes="
      {urls.small ? '(max-width: 600px) 375px,' : ''}
      {urls.medium ? '(max-width: 1500px) 960px,' : ''}
      {urls.large ? '1920px,' : ''}
    "
      {alt}
    />
  </main>
</page>

<style>
  page {
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    box-shadow: 0px 0px 30px 10px rgba(0, 0, 0, 0.3);
    border: 1px solid rgba(255, 255, 255, 0.1);
  }

  main {
    max-height: 500px;
    overflow-y: scroll;
    border-radius: 0 0 10px 10px;
  }

  img {
    max-width: 100%;
    pointer-events: none;
  }

  header {
    background-color: var(--brand-background-secondary);
    border-radius: 10px 10px 0 0;
    padding: 10px 20px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  header .url {
    background-color: var(--brand-background);
    padding: 5px 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: auto;
  }
</style>
