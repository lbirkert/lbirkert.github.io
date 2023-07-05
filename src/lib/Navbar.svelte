<script>
  let scrollY = 0;
</script>

<svelte:window bind:scrollY />

<nav class:detach={scrollY > 10}>
  <div>
    <!--TODO: logo from hero to navbar-->
    <a href="/">
      <picture>
        <source media="(min-resolution: 2x)" srcset="/lucas_3x.webp" />
        <source media="(min-resolution: 1x)" srcset="/lucas_2x.webp" />

        <img src="/lucas_1x.webp" alt="Logo" />
      </picture>
    </a>
    <ul aria-label="links">
      <li>
        <a href="/#projects">Projects</a>
      </li>
      <li>
        <a href="/contact#top">Contact</a>
      </li>
    </ul>
  </div>
</nav>

<style>
  nav {
    width: 100vw;
    position: sticky;
    top: 0;
    left: 0;
    z-index: 100;
    transition: background-color 0.3s ease, box-shadow 0.3s ease;
    background-color: var(--brand-background);
    background: none;
  }

  nav.detach {
    background-color: var(--brand-background-secondary);
    box-shadow: 5px 5px 50px 5px rgba(0, 0, 0, 0.3);
  }

  nav div {
    display: flex;
    width: 90%;
    max-width: 750px;
    margin: auto;
    padding: 10px 0;
  }

  nav ul {
    flex: 1;
    display: flex;
    justify-content: right;
    align-items: center;
    list-style: none;
    column-gap: 30px;
  }

  nav a {
    color: var(--brand-secondary);
    text-decoration: none;
    transition: color 0.3s ease;
  }

  nav a:hover {
    color: var(--brand-primary);
  }

  nav img {
    width: 32px;
    height: 32px;
    border-radius: 20px;
  }
</style>
