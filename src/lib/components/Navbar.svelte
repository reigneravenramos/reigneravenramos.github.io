<script lang="ts">
  import { onMount } from "svelte";
  import { Moon, Sun, Menu, X } from "lucide-svelte";

  let scrolled = false;
  let isDarkMode = true;
  let isMobileMenuOpen = false;
  let activeSection = "";

  const toggleTheme = () => {
    isDarkMode = !isDarkMode;
    document.body.classList.toggle("light-mode");
  };

  const toggleMobileMenu = () => {
    isMobileMenuOpen = !isMobileMenuOpen;
    if (isMobileMenuOpen) {
      document.body.style.overflow = "hidden";
    } else {
      document.body.style.overflow = "";
    }
  };

  const closeMenu = () => {
    isMobileMenuOpen = false;
    document.body.style.overflow = "";
  };

  onMount(() => {
    const handleScroll = () => {
      scrolled = window.scrollY > 20;
    };
    window.addEventListener("scroll", handleScroll);

    // Scroll Spy Logic
    const observerOptions = {
      rootMargin: "-20% 0px -80% 0px",
      threshold: 0,
    };

    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          const id = entry.target.id;
          activeSection = id === "home" ? "" : `#${id}`;
        }
      });
    }, observerOptions);

    document.querySelectorAll("section[id]").forEach((section) => {
      observer.observe(section);
    });

    return () => {
      window.removeEventListener("scroll", handleScroll);
      observer.disconnect();
    };
  });

  const navLinks = [
    { name: "Home", href: "#" },
    { name: "About", href: "#about" },
    { name: "Experience", href: "#experience" },
    { name: "Education", href: "#education" },
    { name: "Skills", href: "#skills" },
    { name: "Projects", href: "#projects" },
  ];
</script>

<nav class:scrolled class:mobile-open={isMobileMenuOpen}>
  <div class="container nav-content">
    <a href="/" class="logo" on:click={closeMenu}>VENS</a>

    <div class="desktop-links">
      {#each navLinks as link}
        <a href={link.href} class:active={activeSection === link.href}
          >{link.name}</a
        >
      {/each}
      <button
        class="theme-toggle"
        on:click={toggleTheme}
        aria-label="Toggle Theme"
      >
        {#if isDarkMode}
          <Moon size={20} />
        {:else}
          <Sun size={20} />
        {/if}
      </button>
    </div>

    <div class="mobile-actions">
      <button
        class="theme-toggle"
        on:click={toggleTheme}
        aria-label="Toggle Theme"
      >
        {#if isDarkMode}
          <Moon size={20} />
        {:else}
          <Sun size={20} />
        {/if}
      </button>
      <button
        class="menu-toggle"
        on:click={toggleMobileMenu}
        aria-label="Toggle Menu"
      >
        {#if isMobileMenuOpen}
          <X size={24} />
        {:else}
          <Menu size={24} />
        {/if}
      </button>
    </div>
  </div>

  <!-- Mobile Menu Overlay -->
  <div class="mobile-menu" class:open={isMobileMenuOpen}>
    <div class="mobile-nav-links">
      {#each navLinks as link}
        <a
          href={link.href}
          class:active={activeSection === link.href}
          on:click={closeMenu}>{link.name}</a
        >
      {/each}
    </div>
  </div>
</nav>

<style lang="scss">
  @use "../styles/theme" as *;

  nav {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 1000;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    padding: $spacing-md 0;
    background: transparent;

    &.scrolled {
      @include glass;
      padding: $spacing-sm 0;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    }

    &.mobile-open {
      background: $bg-primary;
    }
  }

  .nav-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo {
    font-size: 1.5rem;
    font-weight: 900;
    letter-spacing: 2px;
    z-index: 1001;

    &:hover {
      opacity: 1;
      color: $accent-primary;
      text-shadow: 0 0 10px rgba(var(--accent-primary-rgb), 0.3);
    }
  }

  .desktop-links {
    display: flex;
    align-items: center;
    gap: $spacing-md;

    @media (max-width: 768px) {
      display: none;
    }

    a {
      font-size: 0.9rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: 600;
      position: relative;

      &::after {
        content: "";
        position: absolute;
        bottom: -5px;
        left: 0;
        width: 0%;
        height: 2px;
        background: $accent-primary;
        transition: width 0.3s ease;
      }

      &:hover,
      &.active {
        color: $accent-primary;
      }

      &:hover::after,
      &.active::after {
        width: 100%;
      }
    }
  }

  .mobile-actions {
    display: none;
    gap: $spacing-sm;
    align-items: center;
    z-index: 1001;

    @media (max-width: 768px) {
      display: flex;
    }
  }

  .theme-toggle,
  .menu-toggle {
    background: none;
    border: none;
    color: inherit;
    cursor: pointer;
    padding: 0.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;

    &:hover {
      color: $accent-primary;
    }
  }

  .mobile-menu {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: $bg-primary;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transform: translateY(-100%);
    transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    z-index: 1000;

    &.open {
      transform: translateY(0);
    }
  }

  .mobile-nav-links {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: $spacing-lg;

    a {
      font-size: 1.5rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 2px;

      &:hover,
      &.active {
        color: $accent-primary;
      }
    }
  }
</style>
