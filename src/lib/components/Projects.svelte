<script lang="ts">
  import { ArrowUpRight, ChevronDown, ChevronUp } from "lucide-svelte";

  const projects = [
    {
      title: "StudyNet",
      tech: "Java | Android Studio ",
      description:
        "Is an app designed for users to review and learn more about networking concepts. It offers a comprehensive learning experience by providing reviewers on key topics and quizzes to assess user knowledge.",
      link: "https://github.com/ReigneRaven/StudyNET",
    },
    {
      title: "CDKC: Web-based Medical Services",
      tech: "React | MongoDB | Express.js | Node.js",
      description:
        "A web application that streamlines patient–admin interaction by enabling patients to schedule appointments, access medical records, and order medications, while providing admins with tools to manage appointments, patient records, inventory, and reports efficiently.",
      link: "https://github.com/ReigneRaven/CCMDKC-Web",
    },
    {
      title: "CliniQ - Clinic Queueing Management System",
      tech: "React | React Native | Node.js | Express.js | MySQL",
      description:
        "A web and mobile queueing management system designed to revolutionize patient flow, optimize clinical efficiency and enhance the healthcare patient experience.",
      link: "#",
    },
    {
      title: "PCRealm",
      tech: "TypeScript | Babylon.js",
      description:
        "A web system that helps users build their ideal PC setup within budget constraints.",
      link: "#",
    },
    {
      title: "JeepCity",
      tech: "C# | JavaScript | HTML | CSS",
      description:
        "A website with detailed information about Dagupan City's jeepney routes and fares.",
      link: "#",
    },
  ];

  let showAll = false;
  $: visibleProjects = showAll ? projects : projects.slice(0, 4);
</script>

<section id="projects" class="projects reveal">
  <div class="container">
    <h2 class="section-title">PROJECTS</h2>

    <div class="grid">
      {#each visibleProjects as project}
        <div class="card">
          <h3 class="title">{project.title}</h3>
          <span class="tech">{project.tech}</span>

          <p class="description">
            {project.description}
          </p>

          <a
            href={project.link}
            target="_blank"
            rel="noopener noreferrer"
            class="visit-link"
          >
            LINK
            <ArrowUpRight size={18} />
          </a>
        </div>
      {/each}
    </div>

    {#if projects.length > 4}
      <div class="load-more-container">
        <button class="load-more-btn" on:click={() => (showAll = !showAll)}>
          {#if showAll}
            Show Less <ChevronUp size={20} />
          {:else}
            Load More <ChevronDown size={20} />
          {/if}
        </button>
      </div>
    {/if}
  </div>
</section>

<style lang="scss">
  @use "../styles/theme" as *;

  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
    gap: $spacing-lg;

    @media (max-width: 768px) {
      grid-template-columns: 1fr;
    }
  }

  .card {
    @include glass;
    border-radius: 20px; // More rounded like sketch
    padding: $spacing-md;
    display: flex;
    flex-direction: column;
    transition: all 0.3s ease;
    position: relative;
    min-height: 250px;

    &:hover {
      border-color: $accent-primary;
      box-shadow: 0 10px 30px -10px rgba(var(--accent-primary-rgb), 0.2);
    }
  }

  .title {
    font-size: 1.5rem;
    font-weight: 700;
    color: $accent-primary;
    margin: 0;
    letter-spacing: 1px;
  }

  .tech {
    font-size: 0.9rem;
    font-weight: 700;
    color: $accent-secondary;
    margin-bottom: $spacing-sm;
    display: block;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  .description {
    font-size: 1rem;
    color: $text-primary;
    margin-bottom: $spacing-md;
    line-height: 1.6;
    flex-grow: 1;
  }

  .visit-link {
    align-self: flex-end;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 8px 24px;
    border: 1px solid $accent-secondary;
    border-radius: 20px; // Pill shape button
    color: black;
    background: $accent-secondary;

    background: transparent;
    color: $accent-secondary;

    font-weight: 700;
    font-size: 0.9rem;
    letter-spacing: 1px;
    transition: all 0.3s ease;
    text-transform: uppercase;

    display: inline-flex;
    align-items: center;
    gap: 8px;

    &:hover {
      background: $accent-secondary;
      color: black;
      box-shadow: 0 0 15px rgba(var(--accent-secondary-rgb), 0.4);
    }
  }
  .load-more-container {
    display: flex;
    justify-content: center;
    margin-top: $spacing-xl;
  }

  .load-more-btn {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 12px 32px;
    background: transparent;
    border: 1px solid $accent-primary;
    color: $accent-primary;
    border-radius: 30px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all 0.3s ease;
    @include glass;

    &:hover {
      background: $accent-primary;
      color: black;
      box-shadow: 0 0 20px rgba(var(--accent-primary-rgb), 0.3);
      transform: translateY(-2px);
    }

    &:active {
      transform: translateY(0);
    }
  }
</style>
