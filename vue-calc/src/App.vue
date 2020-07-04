<template>
  <div id="app">
    <div class="calculator-body">
      <input type="text" name="output" class="output" v-model="display" :disabled="!disabled">
      <div class="keys">
            <button 
              v-for="(op,index) in ops" 
              v-bind:key="index" 
              class="opkeys"
              @click="printDisplay(op)"
            >{{op}}</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    data(){
      return{
        ops: ["7","8","9","AC","4","5","6","+","1","2","3","-","0",".","/","="],
        display: "",
        disabled: false
      }
    },
    methods: {
      printDisplay(op){
        if(op==="="){
            this.display = eval(this.display);
        }else if(op==="AC"){
            this.display = "";
        }
        else{
          this.display = this.display + op;
        }
      }
    }
}
</script>

<style scoped>
  .calculator-body{
    height: 80vh;
    width: 400px;
    background-color: rgb(54, 122, 182);
    margin: 40px auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .opkeys{
    width: 100px;
    height: 100px;
    color: rgb(54, 122, 182);
    font-size: 25px;
  }
  .output{
    width: 355px;
    height: 100px;
    padding: 20px;
    font-size: 25px;
    background-color: lavenderblush;
    color: cornflowerblue;
  }
</style>
