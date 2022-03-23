<template>
  <q-layout>
    <router-view/>
  </q-layout>
</template>

<script>
import {Options, Vue} from "vue-class-component";

@Options({
  components: {}
})
export default class App extends Vue{

}
</script>

<style>

@font-face {
  font-family: "Decterm";
  src: local("Decterm"),
  url(../src/fonts/_decterm.ttf) format("truetype");
}

::-webkit-scrollbar {
  width: 5px;
}

::-webkit-scrollbar-track {
  background: black;
}

::-webkit-scrollbar-thumb {
  background: #00ef00;
}

::-webkit-scrollbar-thumb:hover {
  background: #00ef00;
}

</style>
