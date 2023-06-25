<script>
  import "@fontsource/inter";
  import "@fontsource/inter/latin-900.css";

  // Import app-wide stylesheet
  import "../app.css";
  import Navbar from "../lib/Navbar.svelte";
  import Footer from "$lib/Footer.svelte";
</script>

<svelte:head>
  <meta name="theme-color" content="#1e1f26" />
  <meta
    name="description"
    content="I am a web and software developer focusing on simplicity. I have got more than 3 years of experience in the programming field."
  />
</svelte:head>

<div id="top" />
<Navbar />
<slot />
<Footer />
