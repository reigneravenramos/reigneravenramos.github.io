<section id="about" class="about reveal">
  <div class="container">
    <h2 class="section-title">ABOUT ME</h2>
    <div class="content">
      <p>
        Hello! I’m <span class="highlight-name">Reigne Raven</span>, an enthusiastic 
        <span class="highlight">Information Technology</span> graduate from 
        <span class="highlight">PHINMA University of Pangasinan</span> with a 
        passion for creating engaging and user-focused web experiences. 
        I specialize in designing and developing modern, responsive websites, 
        supported by a strong foundation in HTML, CSS, Java, and JavaScript.
      </p>
      <p>
        UI/UX design is my core expertise. I design intuitive, accessible, and
        visually cohesive interfaces that emphasize usability and user-centered
        interaction. Through wireframing and prototyping, I effectively
        translate concepts and requirements into structured design solutions
        that enhance user experience and support overall project objectives.
      </p>
      <p>
        I am committed to innovation and constant improvement, aiming to create
        work that not only fulfills project goals but also pushes the boundaries
        of my abilities.
      </p>
    </div>
  </div>
</section>

<style lang="scss">
  @use "../styles/theme" as *;

  .highlight {
    color: $accent-secondary; // or any color you want
    font-weight: 600;
  }

  .highlight-name {
    color: $accent-primary; // or any color you want
    font-weight: 600;
  }
  .content {
    width: 100%;
    background: $bg-secondary;
    padding: $spacing-lg;
    border: 1px solid $border-color;
    border-radius: 20px;
    @include glass;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);

    &:hover {
      border-color: $accent-primary;
      box-shadow: 0 0 30px rgba(var(--accent-primary-rgb), 0.1);
    }

    p {
      margin-bottom: $spacing-md;
      font-size: 1.1rem;

      &:last-child {
        margin-bottom: 0;
      }
    }
  }
</style>
