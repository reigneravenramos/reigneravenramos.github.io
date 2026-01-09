<script lang="ts">
  import Icon from "@iconify/svelte";

  const skillCategories = [
    {
      name: "FRONTEND",
      skills: [
        { name: "Java", icon: "logos:java" },
        { name: "JavaScript", icon: "logos:javascript" },
        { name: "React", icon: "logos:react" },
        { name: "HTML", icon: "logos:html-5" },
        { name: "CSS", icon: "logos:css-3" },
        { name: "Bootstrap", icon: "logos:bootstrap" },
      ],
    },
    {
      name: "BACKEND",
      skills: [
        { name: "Java", icon: "logos:java" },
        { name: "Node.js", icon: "logos:nodejs-icon" },
        { name: "Express.js", icon: "skill-icons:expressjs-dark" },
        { name: "MongoDB", icon: "logos:mongodb-icon" },
        { name: "MySQL", icon: "logos:mysql-icon" },
        { name: "SQLite", icon: "logos:sqlite" },
      ],
    },
    {
      name: "TOOLS",
      skills: [
        { name: "Canva", icon: "simple-icons:canva" },
        { name: "Figma", icon: "logos:figma" },
        { name: "Adobe Photoshop", icon: "logos:adobe-photoshop" },
        { name: "VsCode", icon: "logos:visual-studio-code" },
        { name: "Git", icon: "logos:git-icon" },
        { name: "Eclipse", icon: "logos:eclipse-icon" },
        { name: "Postman", icon: "logos:postman-icon" },
        { name: "WordPress", icon: "logos:wordpress-icon" },
      ],
    },
  ];
</script>

<section id="skills" class="skills reveal">
  <div class="container">
    <h2 class="section-title">SKILLS</h2>

    <div class="categories">
      {#each skillCategories as cat}
        <div class="category">
          <h3 class="cat-name">{cat.name}</h3>
          <div class="skill-list">
            {#each cat.skills as skill}
              <div class="skill-tag">
                <div class="icon-wrapper">
                  <Icon icon={skill.icon} height="28" />
                </div>
                <span>{skill.name}</span>
              </div>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style lang="scss">
  @use "../styles/theme" as *;

  .categories {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: $spacing-lg;
  }

  .cat-name {
    font-size: 1.2rem;
    letter-spacing: 2px;
    color: $text-primary;
    margin-bottom: $spacing-md;
    padding-bottom: $spacing-xs;
  }

  .skill-list {
    display: flex;
    flex-wrap: wrap;
    gap: $spacing-sm;
  }

  .skill-tag {
    @include glass;
    padding: $spacing-xs $spacing-sm;
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 0.9rem;
    font-weight: 500;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    border: 1px solid transparent;
    border-radius: 20px;

    .icon-wrapper {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 28px;
      height: 28px;
      filter: grayscale(0.2) brightness(0.9);
      transition: all 0.3s ease;
    }

    &:hover {
      border-color: $accent-primary;
      background: rgba(var(--accent-primary-rgb), 0.05);
      transform: translateY(-2px);
      box-shadow: 0 4px 15px rgba(var(--accent-primary-rgb), 0.1);

      .icon-wrapper {
        filter: grayscale(0) brightness(1.1);
        transform: scale(1.15);
      }
    }
  }
</style>
