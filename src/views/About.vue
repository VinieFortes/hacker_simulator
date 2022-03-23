<template>
  <q-page class="flex column bg-black">
    <div class="typewriter flex column">
      <h1>HACKER SIMULATOR</h1>
      <p class="text">ESSA APLICAÇÃO WEB É APENAS UM JOGO SEM QUALQUER RELAÇÃO REAL COM INVASÕES DE SISTEMAS E QUEBRA DE SEGURANÇAS</p>
      <p class="text">Feito por Vinie Fortes</p>
      <div class="flex flex-center q-gutter-md">
        <a href="https://www.linkedin.com/in/viniciussfortes/"><img src="https://cdn-icons-png.flaticon.com/512/174/174857.png" width="42" alt="Linkedin"></a>
        <a href="https://github.com/VinieFortes"><img style="background-color: white; border-radius: 22px" src="https://cdn-icons-png.flaticon.com/512/25/25231.png" width="42" alt="Github"></a>
      </div>
    </div>
  </q-page>
</template>

<script lang="ts">
import {Options, Vue} from "vue-class-component";

@Options({
  components: {}
})
export default class About extends Vue{

}
</script>

<style scoped>

* {
  font-family: "Decterm", serif;
}

.text{
  color: #00ef00;
  font-size: 35px;
}

a{text-decoration: none}

h1{
  color: #00ef00;
  text-align: center;
  animation: glitch 1s linear infinite;
}

@keyframes glitch{
  2%,64%{
    transform: translate(2px,0) skew(0deg);
  }
  4%,60%{
    transform: translate(-2px,0) skew(0deg);
  }
  62%{
    transform: translate(0,0) skew(5deg);
  }
}
h1:before,
h1:after{
  content: attr(title);
  position: absolute;
  left: 0;
}

h1:before{
  animation: glitchTop 1s linear infinite;
  clip-path: polygon(0 0, 100% 0, 100% 33%, 0 33%);
  -webkit-clip-path: polygon(0 0, 100% 0, 100% 33%, 0 33%);
}

@keyframes glitchTop{
  2%,64%{
    transform: translate(2px,-2px);
  }
  4%,60%{
    transform: translate(-2px,2px);
  }
  62%{
    transform: translate(13px,-1px) skew(-13deg);
  }
}

h1:after{
  animation: glitchBotom 1.5s linear infinite;
  clip-path: polygon(0 67%, 100% 67%, 100% 100%, 0 100%);
  -webkit-clip-path: polygon(0 67%, 100% 67%, 100% 100%, 0 100%);
}

@keyframes glitchBotom{
  2%,64%{
    transform: translate(-2px,0);
  }
  4%,60%{
    transform: translate(-2px,0);
  }
  62%{
    transform: translate(-22px,5px) skew(21deg);
  }
}

.typewriter p {
  overflow: hidden;
  text-align: center;
  letter-spacing: .15em;
  animation:
      typing 3.5s steps(40, end),
      blink-caret .75s step-end infinite;
}

@keyframes typing {
  from { width: 0; text-align: start }
  to { width: 100%; }
}

</style>
