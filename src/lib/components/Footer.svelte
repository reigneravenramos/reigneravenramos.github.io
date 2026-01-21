<script lang="ts">
  import { Github, Linkedin, Mail } from "lucide-svelte";

  const currentYear = new Date().getFullYear();
</script>

<footer>
  <div class="container">
    <div class="divider"></div>
    <div class="content">
      <p class="copyright">© {currentYear} Reigne Raven Ramos</p>

      <div class="socials">
        <a
          href="https://github.com/reigneravenramos"
          target="_blank"
          rel="noopener noreferrer"
          aria-label="GitHub"
        >
          <Github size={20} />
        </a>
        <a
          href="https://www.linkedin.com/in/reigneravenramos"
          target="_blank"
          rel="noopener noreferrer"
          aria-label="LinkedIn"
        >
          <Linkedin size={20} />
        </a>
        <a href="mailto:reigneraven.ramos@gmail.com " aria-label="Email">
          <Mail size={20} />
        </a>
      </div>
    </div>
  </div>
</footer>

<style lang="scss">
  @use "../styles/theme" as *;

  footer {
    padding: $spacing-lg 0 $spacing-md;
    background-color: $bg-primary;
  }

  .divider {
    height: 1px;
    background: $border-color;
    width: 100%;
    margin-bottom: $spacing-md;
  }

  .content {
    display: flex;
    justify-content: space-between;
    align-items: center;

    @media (max-width: 768px) {
      flex-direction: column;
      gap: $spacing-md;
    }
  }

  .copyright {
    font-size: 0.85rem;
    font-weight: 500;
  }

  .socials {
    display: flex;
    gap: $spacing-md;

    a {
      color: $text-secondary;

      &:hover {
        color: $text-primary;
        transform: translateY(-2px);
      }
    }
  }
</style>
