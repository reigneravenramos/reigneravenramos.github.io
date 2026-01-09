<script lang="ts">
  const experiences = [
    {
      company: "PIXELHUB Design + Digital Agency | Internship",
      position: "GRAPHIC DESIGNER",
      period: "2025",
      details:
        "Played a key role in the design and development of the official website of the Calasiao Local Government Unit (LGU). Additionally, developed wireframes using Figma for the Department of Tourism (DOT) Region III website, with an emphasis on usability and clear visual hierarchy.",
    },
    {
      company: "Capstone Project and Web Development",
      position: "FRONTEND DEVELOPER AND UI/UX DESIGNER",
      period: "2023 - 2024",
      details:
        "Co-developed a web application designed to facilitate seamless interaction between patients and admins. The platform allows patients to easily schedule appointments, access their medical records, and order medications, improving convenience and reducing wait times. In addition, it provides admins with tools to manage appointments, update patient records, oversee inventory, and generate reports, streamlining administrative tasks.",
    },
    {
      company: "New Venture Creation",
      position: "PROJECT MANAGER AND LEAD DESIGNER",
      period: "2024",
      details:
        "Led and proposed a web system that helps users build their ideal PC setup within budget constraints. The application features an interactive simulation tool, allowing users to drag and drop components, check compatibility, and estimate performance level.",
    },
    {
      company: "Junior Final Project Development",
      position: "UI/UX DESIGNER",
      period: "2023",
      details:
        "Co-developed a web and mobile queueing management system, where I led the UI/UX design process crafting intuitive user flows, wireframes, and prototypes—to revolutionize patient flow, optimize clinical efficiency, and enhance the overall healthcare patient experience.",
    },
  ];
</script>

<section id="experience" class="experience reveal">
  <div class="container">
    <h2 class="section-title">EXPERIENCE</h2>

    <div class="timeline">
      {#each experiences as exp, i}
        <div class="item {i % 2 === 0 ? 'left' : 'right'}">
          <div class="dot"></div>
          <div class="content-wrapper">
            <div class="meta">
              <span class="period">{exp.period}</span>
              <h3 class="position">{exp.position}</h3>
              <h4 class="company">{exp.company}</h4>
            </div>
            <div class="details-box">
              <p>{exp.details}</p>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style lang="scss">
  @use "../styles/theme" as *;

  .timeline {
    position: relative;
    max-width: 1000px;
    margin: 0 auto;

    // Center Line
    &::after {
      content: "";
      position: absolute;
      width: 2px;
      background-color: $border-color;
      top: 0;
      bottom: 0;
      left: 50%;
      margin-left: -1px;

      @media (max-width: 768px) {
        left: 20px;
      }
    }
  }

  .item {
    padding: 10px 40px;
    position: relative;
    background-color: transparent;
    width: 50%;
    box-sizing: border-box;

    @media (max-width: 768px) {
      width: 100%;
      padding-left: 50px;
      padding-right: 0;
    }

    &.left {
      left: 0;
      text-align: right;

      .content-wrapper {
        align-items: flex-end;
      }

      .dot {
        right: -7px; // Centered on line (width 12px + 2px border)

        @media (max-width: 768px) {
          left: 15px; // Move to left on mobile
          right: auto;
        }
      }

      @media (max-width: 768px) {
        left: 0;
        text-align: left;

        .content-wrapper {
          align-items: flex-start;
        }
      }
    }

    &.right {
      left: 50%;
      text-align: left;

      .content-wrapper {
        align-items: flex-start;
      }

      .dot {
        left: -7px;

        @media (max-width: 768px) {
          left: 15px;
        }
      }

      @media (max-width: 768px) {
        left: 0;
      }
    }
  }

  .dot {
    position: absolute;
    width: 12px;
    height: 12px;
    background-color: $accent-primary; // Sketch has dots on line
    border-radius: 50%;
    top: 20px; // Align with top meta info
    z-index: 1;

    // Ensure ring effect if desired, or solid
    border: 2px solid $bg-primary;
    box-shadow: 0 0 0 2px $accent-primary;
  }

  .content-wrapper {
    display: flex;
    flex-direction: column;
    gap: $spacing-xs;
  }

  .meta {
    display: flex;
    flex-direction: column;
    gap: 4px;
  }

  .period {
    font-size: 0.9rem;
    font-weight: 700;
    color: $text-primary; // "White" / Theme Aware
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  .position {
    font-size: 1.5rem;
    font-weight: 700;
    color: $accent-primary; // "Senior Dev -> Teal"
    margin: 0;
  }

  .company {
    font-size: 1.1rem;
    font-weight: 600;
    color: $accent-secondary; // "Company -> Gold"
    margin: 0;
    margin-bottom: $spacing-xs;
  }

  .details-box {
    padding: $spacing-md;
    @include glass; // Keep glass effect like sketch box
    border-radius: 20px;
    transition: all 0.3s ease;
    position: relative;
    width: 100%;

    p {
      margin-top: 0;
      font-size: 1rem;
      color: $text-secondary; // Theme aware text
    }

    &:hover {
      border-color: $accent-primary;
      box-shadow: 0 0 20px rgba(var(--accent-primary-rgb), 0.15);
      transform: translateY(-2px);
      // "Teal hover"
    }
  }
</style>
