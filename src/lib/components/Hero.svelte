<script lang="ts">
  import { Github, Linkedin, Mail, ArrowUpRight } from "lucide-svelte";
</script>

<section id="home" class="hero reveal">
  <div class="container">
    <div class="content">
      <h2 class="greeting">HELLO, I'M</h2>
      <h1 class="name">REIGNE RAVEN RAMOS</h1>
      <p class="role">Frontend Developer & UI/UX Designer</p>

      <div class="social-links">
        <a
          href="https://github.com/ReigneRaven"
          target="_blank"
          rel="noopener noreferrer"><Github size={24} /></a
        >
        <a
          href="https://www.linkedin.com/in/reigneravenramos"
          target="_blank"
          rel="noopener noreferrer"><Linkedin size={24} /></a
        >
        <a href="mailto:reigneraven.ramos@gmail.com"><Mail size={24} /></a>
      </div>

      <a href="/cv.pdf" target="_blank" class="cta">
        Curriculum Vitae
        <ArrowUpRight size={20} />
      </a>
    </div>

    <div class="image-wrapper">
      <img src="/resources/venven.png" alt="Profile" class="profile-image" />
    </div>
  </div>
</section>

<style lang="scss">
  @use "../styles/theme" as *;

  .hero {
    min-height: 100vh;
    @include flex-center;
    padding-top: $spacing-xl;
  }

  .container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: $spacing-lg;

    @media (max-width: 768px) {
      flex-direction: column-reverse;
      text-align: center;
    }
  }

  .content {
    flex: 1;
  }

  .greeting {
    font-size: 1.1rem;
    font-weight: 600;
    color: $text-secondary;
    letter-spacing: 6px;
    margin-bottom: $spacing-sm;
    opacity: 0.8;
  }

  .name {
    font-size: 4.5rem;
    line-height: 1;
    margin-bottom: $spacing-sm;
    color: $accent-primary;

    @media (max-width: 768px) {
      font-size: 3rem;
    }
  }

  .role {
    font-size: 1.2rem;
    margin-bottom: $spacing-md;
    font-weight: 400;
    color: $text-secondary;
  }

  .social-links {
    display: flex;
    gap: $spacing-md;
    margin-bottom: $spacing-lg;

    @media (max-width: 768px) {
      justify-content: center;
    }

    a {
      color: $text-secondary;
      &:hover {
        color: $accent-primary;
        transform: translateY(-3px);
      }
    }
  }

  .cta {
    display: inline-block;
    background: transparent;
    color: $accent-secondary;
    border: 1px solid $accent-secondary;
    padding: $spacing-sm $spacing-lg;
    font-weight: 700;
    letter-spacing: 2px;
    cursor: pointer;
    border-radius: 30px;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);

    display: inline-flex;
    align-items: center;
    gap: $spacing-xs;

    &:hover {
      background: $accent-secondary;
      color: black;
      transform: scale(1.02);
      box-shadow: 0 0 20px rgba(var(--accent-secondary-rgb), 0.2);
    }
  }

  .image-wrapper {
    width: 450px;
    height: 450px;
    position: relative;
    border-radius: 50%;
    background: #b8e4f0; // Light blue from reference - keeping as unique element color
    overflow: visible;
    @include flex-center;

    &::after {
      content: "";
      position: absolute;
      inset: -15px;
      border: 2px solid rgba(var(--accent-primary-rgb), 0.2);
      border-radius: 50%;
      z-index: -1;
      transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1);
    }

    &:hover {
      &::after {
        transform: scale(1.05);
        border-color: $accent-primary;
        box-shadow: 0 0 40px rgba(var(--accent-primary-rgb), 0.1);
      }

      .profile-image {
        transform: scale(1.02);
      }
    }

    @media (max-width: 768px) {
      width: 300px;
      height: 300px;
    }
  }

  .profile-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 50%;
    transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1);
  }
</style>
