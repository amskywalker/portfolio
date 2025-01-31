<script setup>
import ufsmonitor from '@/assets/ufsmonitor.png';
import mmorpg from '@/assets/mmorg.png';
import { BiGithub } from "oh-vue-icons/icons";
// const { TweenMax, _ } = window
// /**
//  * Utility function for returning a random integer in a given range
//  * @param {Int} max
//  * @param {Int} min
//  */
// const randomInRange = (max, min) =>
//   Math.floor(Math.random() * (max - min + 1)) + min
// const ACTIVE_PROBABILITY = 0
// const BASE_SIZE = 1
// const VELOCITY_INC = 1.01
// const VELOCITY_INIT_INC = 1.025
// const JUMP_VELOCITY_INC = 1.25
// const JUMP_SIZE_INC = 1.15
// const SIZE_INC = 1.01
// const RAD = Math.PI / 180
// const WARP_COLORS = [
//   [197, 239, 247],
//   [25, 181, 254],
//   [77, 5, 232],
//   [165, 55, 253],
//   [255, 255, 255],
// ]
// /**
//  * Class for storing the particle metadata
//  * position, size, length, speed etc.
//  */
// class Star {
//   STATE = {
//     alpha: Math.random(),
//     angle: randomInRange(0, 360) * RAD,
//   }
//   reset = () => {
//     const angle = randomInRange(0, 360) * (Math.PI / 180)
//     const vX = Math.cos(angle)
//     const vY = Math.sin(angle)
//     const travelled =
//       Math.random() > 0.5
//         ? Math.random() * Math.max(window.innerWidth, window.innerHeight) + (Math.random() * (window.innerWidth * 0.24))
//         : Math.random() * (window.innerWidth * 0.25)
//     this.STATE = {
//       ...this.STATE,
//       iX: undefined,
//       iY: undefined,
//       active: travelled ? true : false,
//       x: Math.floor(vX * travelled) + window.innerWidth / 2,
//       vX,
//       y: Math.floor(vY * travelled) + window.innerHeight / 2,
//       vY,
//       size: BASE_SIZE,
//     }
//   }
//   constructor() {
//     this.reset()
//   }
// }
//
// const generateStarPool = size => new Array(size).fill().map(() => new Star())
//
// // Class for the actual app
// // Not too much happens in here
// // Initiate the drawing process and listen for user interactions 👍
// class JumpToHyperspace {
//   STATE = {
//     stars: generateStarPool(300),
//     bgAlpha: 0,
//     sizeInc: SIZE_INC,
//     velocity: VELOCITY_INC
//   }
//   canvas = document.createElement('canvas')
//   context = this.canvas.getContext('2d')
//   constructor() {
//     this.bind()
//     this.setup()
//     document.body.appendChild(this.canvas)
//     this.render()
//   }
//   render = () => {
//     const {
//       STATE: {
//         bgAlpha,
//         velocity,
//         sizeInc,
//         initiating,
//         jumping,
//         stars,
//       },
//       context,
//       render
//     } = this
//     // Clear the canvas
//     context.clearRect(0, 0, window.innerWidth, window.innerHeight)
//     if (bgAlpha > 0) {
//       context.fillStyle = `rgba(31, 58, 157, ${bgAlpha})`
//       context.fillRect(0, 0, window.innerWidth, window.innerHeight)
//     }
//     // 1. Shall we add a new star
//     const nonActive = stars.filter(s => !s.STATE.active)
//     if (!initiating && nonActive.length > 0) {
//       // Introduce a star
//       nonActive[0].STATE.active = true
//     }
//     // 2. Update the stars and draw them.
//     for (const star of stars.filter(s => s.STATE.active)) {
//       const { active, x, y, iX, iY, iVX, iVY, size, vX, vY } = star.STATE
//       // Check if the star needs deactivating
//       if (
//         ((iX || x) < 0 ||
//           (iX || x) > window.innerWidth ||
//           (iY || y) < 0 ||
//           (iY || y) > window.innerHeight) &&
//         active &&
//         !initiating
//       ) {
//         star.reset(true)
//       } else if (active) {
//         const newIX = initiating ? iX : iX + iVX
//         const newIY = initiating ? iY : iY + iVY
//         const newX = x + vX
//         const newY = y + vY
//         // Just need to work out if it overtakes the original line that's all
//         const caught =
//           (vX < 0 && newIX < x) ||
//           (vX > 0 && newIX > x) ||
//           (vY < 0 && newIY < y) ||
//           (vY > 0 && newIY > y)
//         star.STATE = {
//           ...star.STATE,
//           iX: caught ? undefined : newIX,
//           iY: caught ? undefined : newIY,
//           iVX: caught ? undefined : iVX * VELOCITY_INIT_INC,
//           iVY: caught ? undefined : iVY * VELOCITY_INIT_INC,
//           x: newX,
//           vX: star.STATE.vX * velocity,
//           y: newY,
//           vY: star.STATE.vY * velocity,
//           size: initiating ? size : size * (iX || iY ? SIZE_INC : sizeInc),
//         }
//         let color = `rgba(255, 255, 255, ${star.STATE.alpha})`
//         if (jumping) {
//           const [r, g, b] = WARP_COLORS[randomInRange(0, WARP_COLORS.length)]
//           color = `rgba(${r}, ${g}, ${b}, ${star.STATE.alpha})`
//         }
//         context.strokeStyle = color
//         context.lineWidth = size
//         context.beginPath()
//         context.moveTo(star.STATE.iX || x, star.STATE.iY || y)
//         context.lineTo(star.STATE.x, star.STATE.y)
//         context.stroke()
//       }
//     }
//     requestAnimationFrame(render)
//   }
//   initiate = () => {
//     if (this.STATE.jumping || this.STATE.initiating) return
//     this.STATE = {
//       ...this.STATE,
//       initiating: true,
//       initiateTimestamp: new Date().getTime(),
//     }
//     TweenMax.to(this.STATE, 0.25, {velocity: VELOCITY_INIT_INC, bgAlpha: 0.3})
//     // When we initiate, stop the XY origin from moving so that we draw
//     // longer lines until the jump
//     for (const star of this.STATE.stars.filter(s => s.STATE.active)) {
//       star.STATE = {
//         ...star.STATE,
//         iX: star.STATE.x,
//         iY: star.STATE.y,
//         iVX: star.STATE.vX,
//         iVY: star.STATE.vY,
//       }
//     }
//   }
//   jump = () => {
//     this.STATE = {
//       ...this.STATE,
//       bgAlpha: 0,
//       jumping: true,
//     }
//     TweenMax.to(this.STATE, 0.25, { velocity: JUMP_VELOCITY_INC, bgAlpha: 0.75, sizeInc: JUMP_SIZE_INC })
//     setTimeout(() => {
//       this.STATE = {
//         ...this.STATE,
//         jumping: false,
//       }
//       TweenMax.to(this.STATE, 0.25, { bgAlpha: 0, velocity: VELOCITY_INC, sizeInc: SIZE_INC })
//     }, 2500)
//   }
//   enter = () => {
//     if (this.STATE.jumping) return
//     const { initiateTimestamp } = this.STATE
//     this.STATE = {
//       ...this.STATE,
//       initiating: false,
//       initiateTimestamp: undefined,
//     }
//     if (new Date().getTime() - initiateTimestamp > 600) {
//       this.jump()
//     } else {
//       TweenMax.to(this.STATE, 0.25, {velocity: VELOCITY_INC, bgAlpha: 0})
//     }
//   }
//   bind = () => {
//     this.canvas.addEventListener('mousedown', this.initiate)
//     this.canvas.addEventListener('touchstart', this.initiate)
//     this.canvas.addEventListener('mouseup', this.enter)
//     this.canvas.addEventListener('touchend', this.enter)
//   }
//   setup = () => {
//     this.context.lineCap = 'round'
//     this.canvas.height = window.innerHeight
//     this.canvas.width = window.innerWidth
//   }
//   reset = () => {
//     this.STATE = {
//       ...this.STATE,
//       stars: generateStarPool(300)
//     }
//     this.setup()
//   }
// }
// window.myJump = new JumpToHyperspace()
// window.addEventListener(
//   'resize',
//   _.debounce(() => {
//     window.myJump.reset()
//   }, 250)
// )
</script>

<template>
  <main class="h-full">
    <section class="grid grid-cols-2 grid-rows-1 gap-4 p-4 h-56">
      <div class="personal-information">
        <div class="flex flex-col">
          <h2 class="font-black text-3xl text-yellow-400">Adailton Moura</h2>
          <h4 class="text-2xl text-yellow-400">Back End Engineer</h4>
          <p class="text-yellow-400">Changing the world... <br> Or at least, trying.</p>
        </div>
      </div>
      <div class="social">
        <div class="flex justify-end gap-3">
          <v-icon name="bi-github" class="text-orange-600" scale="2"/>
          <v-icon name="bi-linkedin" class="text-orange-600" scale="2"/>
          <v-icon name="md-email-sharp" class="text-orange-600" scale="2"/>
        </div>
      </div>
    </section>

    <section class="grid grid-cols-[40%_60%] gap-4 p-4">
      <div class="flex flex-col justify-center items-center">
          <div class="flex flex-col text-7xl font-black text-white">
            <span>A</span>
            <span>B</span>
            <span>O</span>
            <span>U</span>
            <span>T</span>
        </div>
      </div>
      <div class="flex flex-col justify-center items-center">
        <div class="flex flex-col text-base font-bold text-white">
          <span class="font-light text-justify">
            Sou um entusiasta da tecnologia que começou sua jornada no desenvolvimento de sistemas
            em 2017, estudando HTML, CSS,  JavaScript e PHP em apostilas na internet. Em 2018,
            ingressei no  Instituto Federal de Ciência e Tecnologia de Sergipe (IFS) no curso de
            Informática, onde adquiri uma base sólida em algoritmos, orientação a  objetos com Java,
            banco de dados com MySQL e noções de engenharia de  software.
            <br>
            <br>
            Em 2020, iniciei minha carreira profissional utilizando PHP 7 e Laravel no backend,
            junto com JavaScript, jQuery e Vue.js no  frontend. Esse período foi fundamental para
            meu crescimento,  consolidando minhas habilidades em desenvolvimento full stack.
            <br>
            <br>
            Atualmente, estou concluindo o curso de  Ciência da Computação na
            Universidade  Federal de Sergipe (UFS), parte fundamental para desenvolver ainda mais
            meus conhecimentos sobre lógica, algoritmos e fundamentos primordiais na área de
            tecnologia. Atuo como analista na SergipeTec, terceirizado para a Procuradoria Geral
            do Município de Aracaju, cujas tecnologias  utlizadas são, Java com Spring Boot,
            Groovy com Grails e Vue js.
            <br>
            <br>
            Meu objetivo principal é me tornar um especialista em backend, afim de continuar
            aprendendo e compartilhando conhecimento, buscando criar  soluções inovadoras que
            impactam positivamente o dia a dia das pessoas.</span>
        </div>
      </div>
    </section>

    <section class="grid grid-cols-[40%_60%] gap-4 p-4 mt-32">
        <div class="flex flex-col justify-center items-center">
          <div class="flex flex-col text-7xl font-black text-white">
            <span>E</span>
            <span>X</span>
            <span>P</span>
            <span>E</span>
            <span>R</span>
            <span>I</span>
            <span>E</span>
            <span>N</span>
            <span>C</span>
            <span>E</span>
            <span>S</span>
          </div>
        </div>
      <div class="flex flex-col justify-start items-start">
        <div class="flex flex-col text-base font-bold text-white">

          <div class="card">
            <h3 class="text-white font-bold text-2xl">Analista de Sistemas Java</h3>
            <p class="text-white text-base font-light text-justify mt-2">Depois de implementar diversas iniciativas de melhoria e padronização de código, implementação de fluxo organizacionais de equipe e práticas de desenvolvimento compatíveis com mercado enquanto estagiário, tive o reconhecimento ao qual me fez poder avançar ainda mais no desenvolvimento do projeto de cobrança de protesto como também a inovação em modernizar as execuções fiscais do município de Aracaju, desenvolvendo um ecossistema com micro serviços necessários para a manutenibilidade, desempenho e monitoramento dos fluxos. Idealizei e implementei serviços de comunicação com a fazenda municipal, serviços de extração de informações em certidões de dívida ativa, serviço de comunicação SOAP com o cartório. Além disso pude impactar diretamente em outros projetos, tanto coordenando, quanto desenvolvendo soluções para problemas recorrentes com integrações em sistemas terceirizados, sanando as dores que persistiam há algum tempo diante dos usuários, assim como realizar a criação de código modelo para a refatoração e upgrade de sistemas legados, para manter a segurança e a eficiência.
            </p>
          </div>

          <div class="card mt-12">
            <h3 class="text-white font-bold text-2xl">Desenvolvedor de Sistemas Java</h3>
            <p class="text-white text-base font-light text-justify mt-2">Depois de implementar diversas iniciativas de melhoria e padronização de código, implementação de fluxo organizacionais de equipe e práticas de desenvolvimento compatíveis com mercado enquanto estagiário, tive o reconhecimento ao qual me fez poder avançar ainda mais no desenvolvimento do projeto de cobrança de protesto como também a inovação em modernizar as execuções fiscais do município de Aracaju, desenvolvendo um ecossistema com micro serviços necessários para a manutenibilidade, desempenho e monitoramento dos fluxos. Idealizei e implementei serviços de comunicação com a fazenda municipal, serviços de extração de informações em certidões de dívida ativa, serviço de comunicação SOAP com o cartório. Além disso pude impactar diretamente em outros projetos, tanto coordenando, quanto desenvolvendo soluções para problemas recorrentes com integrações em sistemas terceirizados, sanando as dores que persistiam há algum tempo diante dos usuários, assim como realizar a criação de código modelo para a refatoração e upgrade de sistemas legados, para manter a segurança e a eficiência.
            </p>
          </div>

          <div class="card mt-12">
            <h3 class="text-white font-bold text-2xl">Estágio em Desenvolvimento de Sistemas Java</h3>
            <p class="text-white text-base font-light text-justify mt-2">Após uma pausa na carreira para aprofundar meus conhecimentos teóricos essenciais ao desenvolvimento como desenvolvedor, tive a oportunidade de estagiar na Procuradoria Geral do Município, onde apliquei na prática conceitos de modelagem de requisitos e engenharia de software. Nesse estágio, iniciei um projeto para modernizar o fluxo de cobrança de protestos da procuradoria, utilizando Java com o framework Spring. Esse trabalho proporcionou uma evolução significativa no meu domínio da linguagem Java e na aplicação de padrões de projeto.</p>
          </div>

          <div class="card mt-12">
            <h3 class="text-white font-bold text-2xl">Desenvolvedor de Sistemas PHP</h3>
            <p class="text-white text-base font-light text-justify mt-2">Graças ao esforço realizado no estágio pude desenvolver minhas habilidades ao ponto de ser contrato, com isso novos desafios foram necessário como dar manutenção em sistemas legados e que me deu uma sólida experiência em melhorias e otimização de código e também me fez colocar em prática os princípios de Clean Code assim tornando o sistema mais eficiente e fácil de manter. Também desenvolvi habilidades em comunicação e trabalho em equipe, além de contribuir com o levantamento de requisitos e estimativas de tarefas, o que facilitou a coordenação e execução dos projetos.</p>
          </div>
            <div class="card mt-12">
              <h3 class="text-white font-bold text-2xl">Estágio em Desenvolvimento de Sistemas Java</h3>
              <p class="text-white text-base font-light text-justify mt-2">Durante esse período de estágio, aperfeiçoei minhas habilidades na linguagem PHP, especialmente ao trabalhar com manutenção de sistemas legados. Aproveitei o período para estudar Laravel e VueJS, o que ampliou bastante o meu conhecimento em frameworks e me permitiu desenvolver integrações entre plataformas utilizando Webhooks e APIs. O período foi essencial para aprimorar tanto minha lógica de programação quanto minha experiência em desenvolvimento e manutenção de aplicações web.</p>
            </div>
        </div>
      </div>
    </section>

    <section class="grid grid-cols-[40%_60%] gap-4 p-4 mt-32">
      <div class="flex flex-col justify-center items-center">
        <div class="flex flex-col text-7xl font-black text-white">
          <span>E</span>
          <span>D</span>
          <span>U</span>
          <span>C</span>
          <span>A</span>
          <span>T</span>
          <span>I</span>
          <span>O</span>
          <span>N</span>
        </div>
      </div>
      <div class="flex flex-col justify-center items-center">
        <div class="flex flex-col text-base font-bold text-white">
          <div class="card">
            <h3 class="text-white font-bold text-2xl">Universidade Federal de Sergipe</h3>
            <p class="text-white text-base font-light text-justify mt-2">Depois de implementar diversas iniciativas de melhoria e padronização de código, implementação de fluxo organizacionais de equipe e práticas de desenvolvimento compatíveis com mercado enquanto estagiário, tive o reconhecimento ao qual me fez poder avançar ainda mais no desenvolvimento do projeto de cobrança de protesto como também a inovação em modernizar as execuções fiscais do município de Aracaju, desenvolvendo um ecossistema com micro serviços necessários para a manutenibilidade, desempenho e monitoramento dos fluxos. Idealizei e implementei serviços de comunicação com a fazenda municipal, serviços de extração de informações em certidões de dívida ativa, serviço de comunicação SOAP com o cartório. Além disso pude impactar diretamente em outros projetos, tanto coordenando, quanto desenvolvendo soluções para problemas recorrentes com integrações em sistemas terceirizados, sanando as dores que persistiam há algum tempo diante dos usuários, assim como realizar a criação de código modelo para a refatoração e upgrade de sistemas legados, para manter a segurança e a eficiência.
            </p>
          </div>

          <div class="card mt-12">
            <h3 class="text-white font-bold text-2xl">Instituto Federal de Ciência e Técnologia de Sergipe</h3>
            <p class="text-white text-base font-light text-justify mt-2">Depois de implementar diversas iniciativas de melhoria e padronização de código, implementação de fluxo organizacionais de equipe e práticas de desenvolvimento compatíveis com mercado enquanto estagiário, tive o reconhecimento ao qual me fez poder avançar ainda mais no desenvolvimento do projeto de cobrança de protesto como também a inovação em modernizar as execuções fiscais do município de Aracaju, desenvolvendo um ecossistema com micro serviços necessários para a manutenibilidade, desempenho e monitoramento dos fluxos. Idealizei e implementei serviços de comunicação com a fazenda municipal, serviços de extração de informações em certidões de dívida ativa, serviço de comunicação SOAP com o cartório. Além disso pude impactar diretamente em outros projetos, tanto coordenando, quanto desenvolvendo soluções para problemas recorrentes com integrações em sistemas terceirizados, sanando as dores que persistiam há algum tempo diante dos usuários, assim como realizar a criação de código modelo para a refatoração e upgrade de sistemas legados, para manter a segurança e a eficiência.
            </p>
          </div>
        </div>
      </div>
    </section>

    <section class="grid grid-cols-[40%_60%] gap-4 p-4 mt-32">
      <div class="flex flex-col justify-center items-center">
        <div class="flex flex-col text-7xl font-black text-white">
          <span>P</span>
          <span>R</span>
          <span>O</span>
          <span>J</span>
          <span>E</span>
          <span>T</span>
          <span>S</span>
        </div>
      </div>
      <div class="flex flex-col justify-center items-center">
        <div class="flex flex-col text-base font-bold text-white">
          <div class="card flex">
            <div class="flex justify-start mr-5">
              <img :src="ufsmonitor" alt="Ufs Monitor" class="w-[92rem] h-[12rem] object-cover">
            </div>
            <div class="flex flex-col">
              <h3 class="text-white font-bold text-2xl">UFS Monitor</h3>
              <p class="text-white text-base font-light text-justify mt-2">
                UFSMonitor é um projeto pessoal que surgiu desde quando entrei na faculdade.
                Por ser curioso e metódico eu andei por toda a universidade para conhecê-la e
                aprender a me localizar, todavia com o passar do tempo percebi que era relativamente
                díficil para calouros e até mesmo para veteranos a própria localização no ambiente UFS.
              </p>
            </div>
          </div>
          <div class="card mt-12 flex">
            <div class="flex justify-start mr-5">
              <img :src="mmorpg" alt="MMORPG" class="w-[111rem] h-[12rem] object-cover">
            </div>
            <div class="flex flex-col">
              <h3 class="text-white font-bold text-2xl">MMORPG</h3>
              <p class="text-white text-base font-light text-justify mt-2">
                O projeto consiste na implementação de um jogo MMORPG baseado no jogo legend online
                que começa na criação da conta, para que o usuário acesse os devidos servidores.

                O mesmo foi realizado na disciplina de Banco de Dados I gerando o aprendizado sobre
                processos de modelagem, geração e customização de DER, avaliação de espaço de memória,
                avaliação de desempenho e trabalho em equipe.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>
