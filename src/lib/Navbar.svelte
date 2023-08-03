<script>
  import Fa from "svelte-fa";
  import { faCode, faPhone } from "@fortawesome/free-solid-svg-icons";
  import { page } from "$app/stores";

  let scrollY = 0,
    innerHeight = 0,
    innerWidth = 0;
  $: isRoot = $page.url.pathname == "/";
</script>

<svelte:window bind:scrollY bind:innerHeight bind:innerWidth />

<nav
  class:detach={scrollY > (isRoot ? innerHeight + innerWidth * 0.2 : 0)}
  class:root={isRoot}
>
  <div>
    <!--TODO: logo from hero to navbar-->
    <a class="logo" href="/">
      <img src="/brand/logo/png/logo_light_square_x64.png" alt="Logo" />
      <h1>Lucas Birkert</h1>
      <p>Web & Software Development</p>
    </a>
    <ul aria-label="links">
      <li>
        <a href="/#projects">
          <Fa icon={faCode} />
          Projects</a
        >
      </li>
      <li>
        <a href="/contact#top">
          <Fa icon={faPhone} />
          Contact</a
        >
      </li>
    </ul>
  </div>
</nav>

<style>
  .logo h1 {
    font-weight: bold;
    margin: 0;
    line-height: 1;
    font-size: 20px;
    margin-right: 10px;
  }

  .logo p {
    font-size: 18px;
    line-height: 1;
  }

  .logo img {
    height: 20px;
    width: 20px;
  }

  nav {
    width: 100vw;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 100;
    transition: background-color 0.3s ease, box-shadow 0.3s ease;
    background-color: var(--brand-background);
    background: none;
  }

  nav.root {
    opacity: 0;
    transition: opacity 0.3s ease;
    pointer-events: none;
  }

  nav.detach {
    background-color: var(--brand-background-secondary);
    box-shadow: 5px 5px 50px 5px rgba(0, 0, 0, 0.3);
    pointer-events: auto;
    opacity: 1;
  }

  nav div {
    display: flex;
    width: 90%;
    max-width: 850px;
    margin: auto;
    padding: 15px 0;
  }

  nav ul {
    flex: 1;
    display: flex;
    justify-content: right;
    align-items: center;
    list-style: none;
    column-gap: 40px;
  }

  @media (max-width: 800px) {
    .logo p {
      display: none;
    }
  }

  @media (max-width: 550px) {
    .logo h1 {
      display: none;
    }
  }

  nav a {
    color: var(--brand-secondary);
    text-decoration: none;
    transition: color 0.3s ease;
    display: flex;
    align-items: center;
    column-gap: 10px;
  }

  nav a h1 {
    margin-bottom: 0;
  }

  nav a:hover {
    color: var(--brand-primary);
  }
</style>
