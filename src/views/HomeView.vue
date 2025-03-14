<script setup>
import ufsmonitor from '@/assets/ufsmonitor.png';
import mmorpg from '@/assets/mmorg.png';
import 'vue3-carousel/dist/carousel.css';
const config = {
  height: 700,
  itemsToShow: 1,
  gap: 5,
  autoplay: 4000,
  wrapAround: true,
  pauseAutoplayOnHover: true,
};
import { Carousel, Slide, Navigation } from 'vue3-carousel';

const experiences = [{
  id: 0,
  title: "Analista de Sistemas Java (2025)",
  description: `
  - Migramos a arquitetura de Spring Rest para Spring GraphQL, reduzindo em 30% o tempo de requisições e tornando o sistema mais adaptável a múltiplos frontends.\n
  - Otimizamos o fluxo de Git Flow, acelerando a homologação das funcionalidades desenvolvidas pela equipe.\n
  - Realizamos a migração de um monólito para microsserviços em Spring Boot, centralizando a gestão de dependências e modernizando o fluxo de trabalho. \n
  - Desenvolvemos uma ferramenta de integração com cartórios municipais, utilizando Java e comunicação SOAP via XML.\n
  - Analisamos e otimizamos queries, aumentando a performance dos sistemas.\n
  - Atualizamos dependências, garantindo confiabilidade e segurança aos projetos.\n
  - Implementamos a prática de Architecture Decision Records (ADR), documentando decisões técnicas estratégicas.
`
  },
  {
    id: 1,
    title: "Desenvolvedor de Sistemas Java (2024 - 2025)",
    description: `
    - Modernização execuções fiscais ao desenvolver um módulo de comunicação com o sistema principal, otimizando o fluxo de +40 mil processos municipais e reduzindo a carga de trabalho geral.\n
    - Desenvolvimento serviços de comunicação com a Fazenda Municipal, incluindo integração SOAP com cartórios, utilizando Spring WebFlux em Java.\n
    - Criação infraestrutura em Cloud privada e dockerizamos 80% dos projetos, aumentando escalabilidade e eficiência.\n
    - Customização o sistema Bookstack para controle interno da equipe, facilitando a documentação dos sistemas, reduzindo o tempo de adaptação de novos integrantes e garantindo confiabilidade aos projetos.\n
    - Construção uma ferramenta de integração com a Fazenda Pública usando Spring Boot (Java), permitindo maior foco na análise processual ao invés da coleta e interpretação manual de informações.\n
    - Desenvolvimento uma ferramenta para atualização de débitos de precatórios municipais com Spring Boot (Java), otimizando cálculos do departamento financeiro e gerando economia para os cofres públicos.\n
    - Implantação uma feature de equilíbrio de demandas administrativas baseada em pesos aninhados, tornando o trabalho da Procuradoria mais justo e eficiente.
 `
  }, {
    id: 3,
    title: "Estágio em Desenvolvimento de Sistemas Java (2023 - 2024)",
    description: `
    -Modernização do fluxo de cobrança de protestos utilizando Java (Spring). \n
    - Correções e automações de fluxos internos da Procuradoria. \n
    - Aplicação de padrões de projeto e conceitos de engenharia de software. \n
    - Análise de melhoria de bancos de dados legados. \n
    - Manutenção em sistema legado utilizando Grails. \n
 `
  }, {
    id: 4,
    title: "Desenvolvedor Web Junior com PHP (2021 - 2022)",
    description: `
    - Manutenção e otimização de sistemas legados com princípios de Clean Code. \n
    - Atualização de versões do Laravel. \n
    - Desenvolvimento de sistemas modernos. \n
    - Participação no levantamento de requisitos e organização de projetos. \n
    - Análise de estimativas de tarefas. \n
 `
  }, {
    id: 5,
    title: "Estágio em Desenvolvimento de Sistemas PHP (2020 - 2021)",
    description: `
    - Manutenção de sistemas legados em PHP e implementação com Laravel e Vue.js. \n
    - Integração entre plataformas utilizando Webhooks e APIs. \n
    `
  }
]

const projects = [{
  id: 0,
  title: "UFS MONITOR",
  image: ufsmonitor,
  description: `
  - Migramos a arquitetura de Spring Rest para Spring GraphQL, reduzindo em 30% o tempo de requisições e tornando o sistema mais adaptável a múltiplos frontends.\n
  - Otimizamos o fluxo de Git Flow, acelerando a homologação das funcionalidades desenvolvidas pela equipe.\n
  - Realizamos a migração de um monólito para microsserviços em Spring Boot, centralizando a gestão de dependências e modernizando o fluxo de trabalho. \n
  - Desenvolvemos uma ferramenta de integração com cartórios municipais, utilizando Java e comunicação SOAP via XML.\n
  - Analisamos e otimizamos queries, aumentando a performance dos sistemas.\n
  - Atualizamos dependências, garantindo confiabilidade e segurança aos projetos.\n
  - Implementamos a prática de Architecture Decision Records (ADR), documentando decisões técnicas estratégicas.
`
  }, {
    id: 1,
    title: "MMORPG",
    image: mmorpg,
    description: `
    - Manutenção de sistemas legados em PHP e implementação com Laravel e Vue.js. \n
    - Integração entre plataformas utilizando Webhooks e APIs. \n
    `
  }
]
</script>

<template>
  <main class="h-full">
    <section class="grid grid-cols-3 grid-rows-1 gap-4 pt-2 mb-10 px-96">
      <div class="folder">
        <div class="flex align-center">
          <v-icon name="bi-folder-fill" class="text-pink-500" scale="1"/>
          <h3 class="text-white text-lg pl-3 text-center">skywalker</h3>
        </div>
        <div class="flex align-center ml-8 mt-2">
          <v-icon name="bi-folder-fill" class="text-pink-500" scale="1"/>
          <h3 class="text-white text-lg pl-3 text-center">adailton</h3>
        </div>
        <div class="flex align-center ml-16 mt-2">
          <v-icon name="bi-folder-fill" class="text-pink-500" scale="1"/>
          <h3 class="text-white text-lg pl-3 text-center">dev</h3>
        </div>
        <div class="flex align-center ml-16 mt-2">
          <v-icon name="bi-folder-fill" class="text-pink-500" scale="1"/>
          <h3 class="text-white text-lg pl-3 text-center">student</h3>
        </div>

      </div>
      <div class="personal-information">
        <div class="flex flex-col">
          <h2 class="text-orange-400 text-3xl cabin-condensed-regular ">Changing the world... <br> Or at least, trying.</h2>
        </div>
      </div>
      <div class="social">
        <div class="flex justify-end gap-3">
          <v-icon name="bi-github" class="text-pink-500" scale="2"/>
          <v-icon name="bi-linkedin" class="text-pink-500" scale="2"/>
          <v-icon name="md-email-sharp" class="text-pink-500" scale="2"/>
        </div>
      </div>
    </section>

    <section class="flex flex-col p-5 px-96">
      <h2 class="text-3xl font-bold text-orange-400 mb-3">ABOUT</h2>
      <div class="flex flex-col text-base font-bold text-white">
        <span class="font-thin text-justify text-xl">
          Desenvolvedor backend com mais de 3 anos de  experiência, especializado em Java – criando projetos com Spring Boot e  mantendo sistemas legados em Grails. Possuo conhecimento prático em PHP  moderno e JavaScript, utilizando a stack Laravue (Laravel + VueJs), além de prática comprovada em ambientes de cloud (AWS e cloud privada),  Docker e fundamentos de Kubernetes. Domínio em GraphQL, microsserviços e gerenciamento de bancos de dados relacionais (MySQL, Postgres) e não  relacionais (MongoDB).
        </span>
      </div>
    </section>

    <section class="flex flex-col mb-15 bg-[#232323] py-10">

      <div class="px-96">
        <h2 class="text-3xl font-bold text-orange-400 mb-5">EXPERIENCES</h2>
        <Carousel v-bind="config">
          <Slide v-for="experience in experiences" :key="experience.id">
            <div class="flex flex-col">
              <h2 class="text-xl font-bold text-white mb-2">{{experience.title}}</h2>
              <div class="flex flex-col text-base font-bold text-white">
              <span class="font-thin text-xl text-justify whitespace-pre-line">
                {{experience.description}}
              </span>
              </div>
            </div>
          </Slide>

          <template #addons>
            <Navigation />
          </template>
        </Carousel>
      </div>
    </section>

    <section class="flex flex-col px-96">
      <h2 class="text-3xl font-bold text-orange-400 mb-5">PROJECTS</h2>
      <Carousel v-bind="config">
        <Slide v-for="project in projects" :key="project.id">
          <div class="flex flex-col">
            <h3 class="text-xl font-bold text-white my-5">{{project.title}}</h3>
            <img :src="project.image" :alt="project.title" />
          </div>
        </Slide>

        <template #addons>
          <Navigation />
        </template>
      </Carousel>
    </section>
    <footer class="flex justify-center text-white mt-10 p-5 bg-[#232323]">
      <p>Desenvolvido com muito ☕ por Adailton Moura</p>
    </footer>
  </main>
</template>
