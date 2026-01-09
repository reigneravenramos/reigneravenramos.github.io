<script lang="ts">
  const education = [
    {
      school: "PHINMA University of Pangasinan",
      degree: "Bachelor of Science in Information Technology",
      period: "July 2021 - July 2025",
      details: "Specialized in Web Development.",
    },
    {
      school: "Joyland School Incorporated",
      degree: "Science, Technology, Engineering, and Mathematics (STEM)",
      period: "Senior Highschool | 2021",
      details: "Graduated with High Honors and Loyalty Awardee.",
    },
    {
      school: "Joyland School Incorporated",
      degree: "Star Section",
      period: "Junior Highschool | 2019",
      details: "Graduated with High Honors and Best in Computer.",
    },
  ];
</script>

<section id="education" class="education reveal">
  <div class="container">
    <h2 class="section-title">EDUCATION</h2>

    <div class="timeline">
      {#each education as edu, i}
        <div class="item {i % 2 === 0 ? 'left' : 'right'}">
          <div class="dot"></div>
          <div class="content-wrapper">
            <div class="meta">
              <span class="period">{edu.period}</span>
              <h3 class="school">{edu.school}</h3>
              <h4 class="degree">{edu.degree}</h4>
            </div>
            <div class="details-box">
              <p>{edu.details}</p>
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
    background-color: $accent-primary;
    border-radius: 50%;
    top: 20px;
    z-index: 1;
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
    color: $text-primary;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  .school {
    font-size: 1.5rem;
    font-weight: 700;
    color: $accent-primary;
    margin: 0;
  }

  .degree {
    font-size: 1.1rem;
    font-weight: 600;
    color: $accent-secondary;
    margin: 0;
    margin-bottom: $spacing-xs;
  }

  .details-box {
    padding: $spacing-md;
    @include glass;
    border-radius: 20px;
    transition: all 0.3s ease;
    position: relative;
    width: 100%;

    p {
      margin-top: 0;
      font-size: 1rem;
      color: $text-secondary;
    }

    &:hover {
      border-color: $accent-primary;
      box-shadow: 0 0 20px rgba(var(--accent-primary-rgb), 0.15);
      transform: translateY(-2px);
    }
  }
</style>
