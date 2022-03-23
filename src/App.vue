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
  url(./fonts/_decterm.ttf) format("truetype");
}

</style>
