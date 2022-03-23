<template>
  <q-page class="flex flex-center column bg-black">
    <div class="typewriter">
      <h1 class="titulo">Hacker Simulator</h1>
    </div>
    <div class="subs">
     <router-link to="/t"><h3 class="sub">__start</h3></router-link>
      <h3 class="sub">__about</h3>
    </div>
  </q-page>
</template>

<script>
import {Options, Vue} from "vue-class-component";

@Options({
  components: {}
})
export default class Home extends Vue{

}
</script>

<style scoped>

* {
  font-family: "Decterm", serif;
}

.titulo, .sub{
  color: #00ef00;
}

a{
  text-decoration: none;
}

.typewriter h1 {
  overflow: hidden;
  white-space: nowrap;
  margin: 0 auto;
  letter-spacing: .15em;
  animation:
      typing 3.5s steps(40, end),
      blink-caret .75s step-end infinite;
}

@keyframes typing {
  from { width: 0 }
  to { width: 100% }
}

.subs{
  visibility: hidden;
  animation: 3.6s fadeIn;
  animation-fill-mode: forwards;
}
@keyframes fadeIn {
  99% {
    visibility: hidden;
  }
  100% {
    visibility: visible;
  }
}

</style>