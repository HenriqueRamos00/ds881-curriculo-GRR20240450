<script setup lang="ts">
const experiences = [
  {
    company: 'Lactec',
    location: 'Curitiba, Paraná, Brasil · Híbrido',
    roles: [
      {
        title: 'Pesquisador júnior',
        type: 'Tempo integral',
        period: 'mai de 2026 - o momento',
        description: 'Pesquisa aplicada com foco em Python e visão computacional.',
      },
      {
        title: 'Estagiário',
        type: 'Estágio',
        period: 'set de 2025 - mai de 2026',
        description: 'Atuação em Python e visão computacional.',
      },
    ],
  },
  {
    company: 'Celepar',
    location: 'Curitiba, Paraná, Brasil · No local',
    roles: [
      {
        title: 'Estagiário',
        type: 'Estágio',
        period: 'mar de 2025 - ago de 2025',
        description: 'Experiência prática em ambiente público de tecnologia.',
      },
    ],
  },
  {
    company: 'Secretaria de Estado da Ciência, Tecnologia e Ensino Superior do Paraná',
    location: 'Curitiba, Paraná, Brasil · No local',
    roles: [
      {
        title: 'Estagiário',
        type: 'Estágio',
        period: 'set de 2024 - fev de 2025',
        description: 'Apoio a atividades ligadas à ciência, tecnologia e ensino superior.',
      },
    ],
  },
]

const education = [
  {
    institution: 'Universidade Federal do Paraná',
    degree: 'Curso Superior de Tecnologia (CST), Computer Systems Analysis',
    period: '2024 - o momento',
  },
  {
    institution: 'Universidade Estadual de Campinas',
    degree: 'Bacharelado, Physics',
    period: '2018 - 2023',
  },
]
</script>

<template>
  <main class="resume-page">
    <section class="hero">
      <div class="hero__content">
        <p class="eyebrow">Currículo</p>
        <h1>Henrique Ramos</h1>
        <p class="hero__summary">
          Pesquisador júnior e estudante de Análise de Sistemas, com experiência em Python, visão
          computacional e tecnologia no setor público.
        </p>
      </div>

      <aside class="hero__panel" aria-label="Resumo profissional">
        <span>Curitiba, Paraná</span>
        <strong>Pesquisa · Tecnologia · Computação</strong>
      </aside>
    </section>

    <section class="section">
      <div class="section__heading">
        <p class="eyebrow">Experiência</p>
        <h2>Trajetória profissional</h2>
      </div>

      <div class="timeline">
        <article v-for="experience in experiences" :key="experience.company" class="timeline__item">
          <div class="timeline__marker" aria-hidden="true"></div>

          <div class="timeline__content">
            <div class="timeline__company">
              <h3>{{ experience.company }}</h3>
              <p>{{ experience.location }}</p>
            </div>

            <div class="role-list">
              <div
                v-for="role in experience.roles"
                :key="`${experience.company}-${role.title}-${role.period}`"
                class="role"
              >
                <div>
                  <h4>{{ role.title }}</h4>
                  <p>{{ role.type }}</p>
                </div>
                <span>{{ role.period }}</span>
                <p class="role__description">{{ role.description }}</p>
              </div>
            </div>
          </div>
        </article>
      </div>
    </section>

    <section class="section section--education">
      <div class="section__heading">
        <p class="eyebrow">Formação acadêmica</p>
        <h2>Educação</h2>
      </div>

      <div class="education-grid">
        <article v-for="item in education" :key="item.institution" class="education-card">
          <p>{{ item.period }}</p>
          <h3>{{ item.institution }}</h3>
          <span>{{ item.degree }}</span>
        </article>
      </div>
    </section>
  </main>
</template>

<style scoped>
:global(*) {
  box-sizing: border-box;
}

:global(body) {
  margin: 0;
  min-width: 320px;
  color: #18211f;
  background:
    linear-gradient(135deg, rgba(29, 100, 87, 0.12), rgba(198, 78, 44, 0.08)),
    #f7f6f2;
  font-family:
    Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

:global(#app) {
  min-height: 100vh;
}

.resume-page {
  width: min(1120px, calc(100% - 40px));
  margin: 0 auto;
  padding: 56px 0;
}

.hero {
  display: grid;
  grid-template-columns: minmax(0, 1fr) 320px;
  gap: 32px;
  align-items: end;
  min-height: 360px;
  padding: 56px;
  color: #f8fbf8;
  background:
    linear-gradient(rgba(19, 42, 39, 0.78), rgba(19, 42, 39, 0.78)),
    linear-gradient(135deg, #123c36, #ba5a3f);
  border-radius: 8px;
  box-shadow: 0 24px 70px rgba(31, 37, 35, 0.16);
}

.hero__content {
  max-width: 720px;
}

.eyebrow {
  margin: 0 0 12px;
  color: #c85d3f;
  font-size: 0.78rem;
  font-weight: 800;
  letter-spacing: 0;
  text-transform: uppercase;
}

.hero .eyebrow {
  color: #f3c6b6;
}

h1,
h2,
h3,
h4,
p {
  margin-top: 0;
}

h1 {
  margin-bottom: 20px;
  font-size: 5.8rem;
  line-height: 0.95;
  letter-spacing: 0;
}

.hero__summary {
  max-width: 680px;
  margin-bottom: 0;
  color: #dfeae5;
  font-size: 1.18rem;
  line-height: 1.7;
}

.hero__panel {
  display: grid;
  gap: 10px;
  padding: 24px;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.18);
  border-radius: 8px;
  backdrop-filter: blur(18px);
}

.hero__panel span {
  color: #c9d8d3;
  font-size: 0.95rem;
}

.hero__panel strong {
  color: #ffffff;
  font-size: 1.35rem;
  line-height: 1.3;
}

.section {
  display: grid;
  grid-template-columns: 280px minmax(0, 1fr);
  gap: 40px;
  padding: 72px 0 0;
}

.section__heading {
  position: sticky;
  top: 28px;
  align-self: start;
}

.section__heading h2 {
  margin-bottom: 0;
  color: #14211e;
  font-size: 2.1rem;
  line-height: 1.12;
}

.timeline {
  display: grid;
  gap: 28px;
}

.timeline__item {
  position: relative;
  display: grid;
  grid-template-columns: 28px minmax(0, 1fr);
  gap: 20px;
}

.timeline__item::before {
  position: absolute;
  top: 24px;
  bottom: -28px;
  left: 6px;
  width: 2px;
  background: #d8d5cc;
  content: "";
}

.timeline__item:last-child::before {
  display: none;
}

.timeline__marker {
  position: relative;
  z-index: 1;
  width: 14px;
  height: 14px;
  margin-top: 8px;
  background: #c85d3f;
  border: 3px solid #f7f6f2;
  border-radius: 50%;
  box-shadow: 0 0 0 4px rgba(200, 93, 63, 0.16);
}

.timeline__content,
.education-card {
  padding: 28px;
  background: rgba(255, 255, 255, 0.72);
  border: 1px solid rgba(24, 33, 31, 0.08);
  border-radius: 8px;
}

.timeline__company {
  display: flex;
  gap: 20px;
  align-items: flex-start;
  justify-content: space-between;
  padding-bottom: 22px;
  border-bottom: 1px solid #dedbd2;
}

.timeline__company h3,
.education-card h3 {
  margin-bottom: 8px;
  color: #132a27;
  font-size: 1.45rem;
  line-height: 1.2;
}

.timeline__company p,
.role p,
.education-card p,
.education-card span {
  color: #69736f;
  line-height: 1.55;
}

.timeline__company p,
.role p,
.education-card p {
  margin-bottom: 0;
}

.role-list {
  display: grid;
  gap: 22px;
  padding-top: 22px;
}

.role {
  display: grid;
  grid-template-columns: minmax(0, 1fr) auto;
  gap: 10px 20px;
}

.role h4 {
  margin-bottom: 4px;
  color: #21302d;
  font-size: 1.05rem;
}

.role span {
  color: #38534e;
  font-size: 0.95rem;
  font-weight: 700;
  white-space: nowrap;
}

.role__description {
  grid-column: 1 / -1;
}

.section--education {
  padding-bottom: 56px;
}

.education-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 20px;
}

.education-card p {
  color: #c85d3f;
  font-size: 0.92rem;
  font-weight: 800;
}

.education-card span {
  display: block;
}

@media (max-width: 840px) {
  .resume-page {
    width: min(100% - 28px, 680px);
    padding: 28px 0;
  }

  .hero,
  .section {
    grid-template-columns: 1fr;
  }

  .hero {
    min-height: auto;
    padding: 36px 24px;
  }

  h1 {
    font-size: 4.4rem;
  }

  .section {
    gap: 24px;
    padding-top: 48px;
  }

  .section__heading {
    position: static;
  }

  .education-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 560px) {
  .resume-page {
    width: calc(100% - 24px);
    padding: 12px 0 28px;
  }

  .hero {
    padding: 28px 20px;
  }

  h1 {
    font-size: 3rem;
  }

  .hero__summary {
    font-size: 1rem;
  }

  .timeline__item {
    grid-template-columns: 18px minmax(0, 1fr);
    gap: 14px;
  }

  .timeline__item::before {
    left: 5px;
  }

  .timeline__content,
  .education-card {
    padding: 22px;
  }

  .timeline__company,
  .role {
    display: grid;
    grid-template-columns: 1fr;
  }

  .role span {
    white-space: normal;
  }
}
</style>
