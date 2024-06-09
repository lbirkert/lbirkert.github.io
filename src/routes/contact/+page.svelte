<main>
  <div>
    <h1>Contact</h1>

    <p>
      For inquiries, collaborations, or just a friendly conversation,
      feel free to reach out to me! You can contact me via email at
      <a href="mailto:lucasbirkert@gmail.com">lucasbirkert@gmail.com</a>
      for a prompt response. Additionally, I'm available on <a href="https://discord.gg/Cq2UpzeTnm">Discord</a>
      – drop me a message, and let's connect. I'm excited to discuss potential projects,
      share ideas, or answer any questions you may have. Looking forward to hearing from you!
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
  <path
    id="hline"
    d="m -1.6702741,163.66963 c 0,0 22.8354941,-31.58985 40.3040271,-35.83995 18.234713,-4.4365 35.818903,14.94595 54.556512,13.90226 21.351405,-1.18928 38.709505,-20.9064 60.023005,-22.64756 19.25633,-1.57311 56.83154,11.38871 56.83154,11.38871"
  />
</svg>

<style>
  main {
    padding: 80px 0;
    padding-top: 120px;
    max-width: 850px;
    width: 90%;
    margin: auto;
    display: flex;
    column-gap: 30px;
  }

  @media (max-width: 550px) {
    main {
      padding: 60px 0;
      padding-top: 100px;
    }
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
    background-color: var(--brand-background-secondary);
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
