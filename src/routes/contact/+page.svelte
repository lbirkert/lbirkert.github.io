<main>
  <div>
    <h1>Contact</h1>

    <p>
      Please consider contacting me via <a href="mailto:lucas.birkert@gmail.com"
        >email</a
      > only
    </p>

    <br />

    <ul>
      <li>to talk about freelancing work</li>
      <li>to propose a job offer</li>
      <li>to report copyright enfirghtements</li>
      <li>to discuss legal issues with this site</li>
    </ul>

    <br />

    <p>
      You may also join my <a href="https://discord.gg/Cq2UpzeTnm"
        >Discord Server</a
      >.
    </p>

    <br />
    <br />
  </div>

  <iframe
    title="Discord Widget"
    src="https://discord.com/widget?id=874319461988069387&theme=dark"
    width="350"
    height="500"
    allowtransparency={true}
    frameborder="0"
    sandbox="allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts"
  />
</main>

<svelte:head>
  <title>Lucas Birkert | Contact</title>
</svelte:head>

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

<style>
  main {
    padding-top: 60px;
    padding-bottom: 60px;
    max-width: 750px;
    width: 90%;
    margin: auto;
    display: flex;
    column-gap: 30px;
  }

  ul {
    margin-left: 20px;
    display: flex;
    flex-direction: column;
    row-gap: 5px;
  }

  iframe {
    margin-left: auto;
    border: 1px solid rgba(100, 100, 100, 0.3);
    border-radius: 6px;
  }

  @media (max-width: 800px) {
    main {
      flex-direction: column;
    }

    iframe {
      width: 100%;
    }
  }
</style>
