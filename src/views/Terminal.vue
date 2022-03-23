<template>
  <q-page class="flex column bg-black">
    <div class="flex row">
      <div class="typewriter">
        <h5 class="txt no-margin">{{ userName }}@{{ userPc }}:</h5>
      </div>
      <div v-show="showCadastroUser === false" class="flex row items-center">
        <q-icon color="white" size="sm" name="chevron_right"></q-icon>
        <input @keyup.enter.native="run" class="input" type="text" maxlength="12" v-model="terminal" autofocus autocomplete="off"/>
      </div>
    </div>
    <div id="Pai" class="flex column">
      <div v-if="showProgressBar" class="bar"><div class="in"></div></div>
    </div>
    <CadastroUser v-show="showCadastroUser" @close="close()"/>
  </q-page>
</template>

<script lang="ts">
import {Options, Vue} from "vue-class-component";
import CadastroUser from "@/components/CadastroUser.vue";

@Options({
  components: {CadastroUser}
})
export default class Terminal extends Vue{

  showCadastroUser = true
  userName = 'user'
  userPc = 'pcUser'

  terminal = ''

  retrievedObject: any;
  dadosObjs: any;

  showProgressBar = false;

  close(){
    this.showCadastroUser = false
    this.retrievedObject = window.localStorage.getItem('dados')
    this.dadosObjs = JSON.parse(this.retrievedObject);
    this.userName = this.dadosObjs.userName
    this.userPc = this.dadosObjs.pcName
  }

  mounted(){
    if(window.localStorage.getItem('dados')){
      this.showCadastroUser = false
      this.retrievedObject = window.localStorage.getItem('dados')
      this.dadosObjs = JSON.parse(this.retrievedObject);
      this.userName = this.dadosObjs.userName
      this.userPc = this.dadosObjs.pcName
    }
  }

  createText(args: string, no_padding: boolean){
    const elPai = document.getElementById('Pai');
    const dateSpan = document.createElement('p');
    dateSpan.id = 'text';
    dateSpan.innerHTML = args
    const style = document.createElement('style');
    style.innerHTML = '@keyframes typing {from { width: 0 }to { width: 100% }}'
    no_padding ? dateSpan.style.cssText = `color: #00ef00; border: red solid; font-size: 20px; text-align: justify; padding: 0; margin: 0; animation: typing 5.5s steps(90, end),blink-caret .75s step-end infinite;@keyframes typing {from { width: 0 }to { width: 100% }}` : dateSpan.style.cssText = `color: #00ef00; font-size: 20px; text-align: justify; padding: 5px; overflow-wrap: break-word; animation: typing 5.5s steps(90, end),blink-caret .75s step-end infinite;@keyframes typing {from { width: 0 }to { width: 100% }}`
    dateSpan.appendChild(style)
    elPai?.appendChild(dateSpan)
  }

  removeText(){
    if(document.getElementById('text')){
      document.getElementById('text')!.remove()
    }
  }


  run(){
    switch (this.terminal){
      case 'matrix':
        this.removeText()
        let text = ''
        for(let i = 1; i < 200; i++){
           text += '011010 101010 1010 0101 0101'
        }
        this.createText(text, false)
        this.terminal = '';
        break

      case 'clear':
        this.removeText()
        this.terminal = '';
        break

      case 'clock':
        this.removeText()
        const today = new Date();
        const time = today.getHours() + "h:" + today.getMinutes() + 'min';
        const date = today.getDate()  + '-' +(today.getMonth() + 1) +  '-' + today.getFullYear();
        this.createText(time + '  ' +date, false)
        this.terminal = '';
        break

      case 'help':
        this.removeText()
        this.createText("<strong>lista de comandos</strong><br>" +
            "clock -- Mostra a hora e data. <br>" +
            "clear -- Limpa o terminal. <br>" +
            "matrix -- Mostra um monte de codigo binario aleatorio.", false)
        this.terminal = '';
        break

      case 'scanIPs':
          this.removeText()
          this.createText(`Buscando IP's na sua rede`, false)
          this.showProgressBar = true;
          // setInterval(() => {
          //   this.createText(`IP 1`, true)
          // },3000);
          this.terminal = '';
        break
    }
  }


}
</script>

<style scoped>

* {
  font-family: "Decterm", serif;
}

.txt{
  color: #00ef00;
  font-size: 20px;
  padding: 5px;
}

.typewriter h5 {
  overflow: hidden;
  white-space: nowrap;
  animation:
      typing 1.5s steps(90, end),
      blink-caret .75s step-end infinite;
}

@keyframes typing {
  from { width: 0 }
  to { width: 100% }
}

.text{
  color: #00ef00;
  font-size: 20px;
  text-align: justify;
  padding: 5px;
  overflow-wrap: break-word;
  animation:
      typing 5.5s steps(90, end),
      blink-caret .75s step-end infinite;
}

.input{
  width: 100%;
  flex: 1;
  border: none;
  font-size: 18px;
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

.bar {
  border: 1px solid #666;
  height: 20px;
  width: 100%;
}

.in {
  animation: fill 10s linear 1;
  height: 100%;
  background-color: #00ef00;
}

@keyframes fill {
  0% {
    width: 0;
  }
  100% {
    width: 100%;
  }
}

</style>