<script lang="ts">
  import { page } from "$app/stores";

  $: isRoot = $page.url.pathname == "/";
</script>

<footer class:root={isRoot}>
  <div>
    <img src="/brand/logo/svg/logo_dark_square.svg" alt="logo" />
    <p>
      Lucas Birkert is a passionate web and software developer who has started
      teaching himself programming in 2020. Since then he has grown to finish
      numerous projects in the web, software, mobile and automation branche.
    </p>
  </div>
  <br />
  <br />
  <br />
  <p>
    &copy; <strong>Lucas Birkert</strong> 2023 | <a href="/imprint">Imprint</a>
  </p>
</footer>

<style>
  footer {
    background-color: var(--brand-background-secondary);
    padding: 30px 20px;
    padding-top: 60px;
    text-align: center;
  }

  footer.root {
    border-top: 2px solid rgba(200, 200, 200, 0.08);
  }

  div {
    display: flex;
    align-items: center;
    margin: auto;
    max-width: 525px;
    text-align: left;
    column-gap: 40px;
    row-gap: 40px;
  }

  img {
    height: 110px;
  }

  @media (max-width: 650px) {
    div {
      flex-direction: column;
      text-align: center;
      max-width: 500px;
    }
  }
</style>
