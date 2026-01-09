<script lang="ts">
  import Navbar from "$lib/components/Navbar.svelte";
  import Footer from "$lib/components/Footer.svelte";
  import { onMount } from "svelte";

  onMount(() => {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("revealed");
          }
        });
      },
      { threshold: 0.1 },
    );

    document.querySelectorAll(".reveal").forEach((el) => observer.observe(el));
  });
</script>

<svelte:head>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link
    rel="preconnect"
    href="https://fonts.gstatic.com"
    crossorigin="anonymous"
  />
  <link
    href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&family=Outfit:wght@100..900&display=swap"
    rel="stylesheet"
  />
  <title>Raven Ramos</title>
</svelte:head>

<div class="app-layout">
  <div class="bg-gradient"></div>
  <Navbar />

  <main>
    <slot />
  </main>

  <Footer />
</div>

<style lang="scss">
  @use "$lib/styles/theme" as *;

  // Global styles
  @use "../lib/styles/app.scss";

  :global(html, body) {
    background-color: var(--bg-primary);
    color: var(--text-primary);
  }

  .app-layout {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    position: relative;
    overflow-x: hidden;
  }

  .bg-gradient {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    background: var(--bg-primary);
    transition: background 0.3s ease;
  }

  main {
    flex: 1;
  }
</style>
