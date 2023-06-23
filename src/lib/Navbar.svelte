<nav>
  <div>
    <a href="/"><img src="logo.svg" alt="Logo" /></a>
    <ul aria-label="links">
      <li>
        <a href="/contact">Projects</a>
      </li>
      <li>
        <a href="/projects">Contact</a>
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
    background-color: var(--brand-background);
    z-index: 100;
  }

  nav div {
    display: flex;
    width: 90%;
    max-width: 600px;
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
  }

  nav img {
    width: 32px;
    height: 32px;
  }
</style>
