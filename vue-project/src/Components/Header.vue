<template>
  <div class="container">
    <h3>Todo List</h3>
    <div class="inputs">
        <input type="text" placeholder="Enter Todo.." class="input" v-model="value">
        <button @click="addTodo(list)" class="button">Add</button>
    </div>
  </div>
</template>

<script>
import {gsap} from 'gsap';
export default{
  props:["list"],
  data(){
    return{
      value:"",
    }
  },
  methods:{
    addTodo(list){
      if(this.value === "") return;

      list.push(this.value);
      this.value = "";
    }
  },
  mounted(){
    gsap.from(
      ".button,.input",{x:300,duration:1,backgroundColor:"blue"}
    );
  }
}
</script>

<style scoped>
.container{
  position: relative;
  left: 50%;
  transform: translateX(-50%);
  width: 300px;
  height: 180px;
  background-color: darkblue;
  border-radius: 5px 5px 0 0;
  margin-top: 50px;
  border:2px solid darkblue;
  border-bottom: none;
}

.container h3{
  width: 100%;
  text-align: center;
  position: relative;
  margin: auto;
  padding: 30px 0 50px 0;
  color: white;
}

button,input{
  border: none;
  outline: none;
}

button,input:focus{
  border: none;
  outline: none;
}

.container .inputs{
  width: 100%;
  text-align: center;
}

.container .inputs input{
  padding: 5px 10px;
  border-radius: 5px 0 0 5px;
  font-weight: bold;
}

.container .inputs button{
  border-radius: 0 5px 5px 0;
  padding: 5px 10px;
  background-color: lightgreen;
  font-weight: bold;
  cursor: pointer;
}

.container .inputs button:hover{
  background-color: lime;
}

</style>
