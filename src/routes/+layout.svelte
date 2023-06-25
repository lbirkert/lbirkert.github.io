<script>
  // Display font
  import "@fontsource/bebas-neue";
  // Primary font
  import "@fontsource/inter";
  import "@fontsource/inter/latin-900.css";

  // Import app-wide stylesheet
  import "../app.css";
  import Navbar from "../lib/Navbar.svelte";
  import Footer from "$lib/Footer.svelte";
</script>

<div id="top" />
<Navbar />
<slot />
<Footer />
