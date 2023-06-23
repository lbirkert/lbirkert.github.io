<script>
  // Display font
  import "@fontsource/abril-fatface";
  // Primary font
  import "@fontsource/quicksand";

  // Import app-wide stylesheet
  import "../app.css";
  import Navbar from "../lib/Navbar.svelte";
</script>

<Navbar />
<slot />
