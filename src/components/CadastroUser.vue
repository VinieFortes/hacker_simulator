<template>
  <div class="window flex column">
    <div class="typewriter">
      <h5 class="flex row txt no-margin">Olá Hacker, para que você possa explorar as falhas da matrix é importante saber seu nickname: </h5>
      <div class="flex row items-center">
        <q-icon color="white" size="sm" name="chevron_right"></q-icon>
        <input @keyup.enter.native="onEnterOne" id="inputName" class="input" type="text" maxlength="12" v-model="dados.userName" :autofocus="nameFocus" :disabled="NameDisabled" autocomplete="off"/>
      </div>
    </div>
    <div v-show="showStepTwo" class="typewriter">
      <h5 class="flex row txt no-margin">Certo {{dados.userName}} agora digite o nome do seu PC:  </h5>
      <div class="flex row items-center">
        <q-icon color="white" size="sm" name="chevron_right"></q-icon>
        <input @keyup.enter.native="onEnterTwo" id="inputPC" class="input" type="text" maxlength="12" v-model="dados.pcName" :autofocus="pcFocus" :disabled="pcDisabled" autocomplete="off"/>
      </div>
    </div>
    <div v-if="showStepThree">
      <h5 class="flex row txt no-margin">Legal {{dados.userName}} configuramos o PC como {{dados.pcName}} esta tudo pronto para começar a hackear ! </h5>
    </div>
    <div class="flex row justify-between q-pt-md q-pl-sm q-pr-sm">
      <span v-show="showStepThree" @click="$emit('close')" style="cursor: pointer" class="sub">__close</span>
      <span class="info">Enter para continuar</span>
    </div>
  </div>
</template>

<style>
</style>

<script lang="ts">
import {Vue} from "vue-class-component";
import { Emit } from 'vue-property-decorator'

export default class CadastroUser extends Vue{

  dados = {
    userName: '',
    pcName: ''
  }
  showStepTwo = false
  showStepThree = false

  NameDisabled = false
  pcDisabled = false

  nameFocus = true
  pcFocus = false

  @Emit("close")
  close(){
    return true;
  }

  onEnterOne(){
    this.nameFocus = false
    this.NameDisabled = true
    this.showStepTwo = true
    this.pcFocus = true
  }

  onEnterTwo(){
    this.showStepThree = true
    this.pcDisabled = true
    window.localStorage.setItem('dados', JSON.stringify(this.dados))
  }



}
</script>

<style scoped>

.window{
  border: #00ef00 solid 5px ;
  width: min-content;
}

.txt{
  color: #00ef00;
  font-size: 25px;
  font-weight: bold;
  padding: 5px;
}

.info, .sub{
  color: #00ef00;
}


.typewriter h5 {
  overflow: hidden;
  white-space: nowrap;
  caret-shape: underscore;
  animation:
      typing 1.5s steps(30, end),
      blink-caret .75s step-end infinite;
}

.input{
  width: 100%;
  flex: 1;
  border: none;
  font-size: 24px;
  caret-color: #00ef00;
  background-color: black;
  color: #00ef00;
}

.input:focus{
  outline: none;
}

@keyframes typing {
  from { width: 0 }
  to { width: 100% }
}

</style>
