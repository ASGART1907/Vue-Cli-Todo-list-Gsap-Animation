<template>
  <div class="container">
    <ul  v-for="item in list" :key="item">
      <li class="item">
         {{ item }} 
         <div class="icons">
           <i class="fas fa-trash-alt" @click="changeListStatus('Remove',$event)"></i> 
           <i class="fas fa-square" @click="changeListStatus('check',$event)"></i>
         </div>
      </li>
    </ul>
   
   <strong v-show="list.length === 0">
     Liste boş...
   </strong>
  </div>
</template>

<script>
import {gsap} from 'gsap';
export default{
  props:["list"],
  data(){
    return{
    }
  },
  methods:{
    changeListStatus(direction,$event){
      const item = $event.target.parentElement.parentElement;

      
      if(direction === "Remove"){
        item.remove();
      }else if(direction === "check"){
        const icon = $event.target;
        
        if(icon.classList.contains("fa-square")){
             icon.setAttribute("class","fas fa-square-check");
             item.setAttribute("id","check");
        }else{
             icon.setAttribute("class","fas fa-square");
             item.setAttribute("id","notCheck");
        }

      }
    }
  },
  mounted(){
    gsap.from(".container",{x:300,duration:1,opacity:0,scale:0.1});
  }
}
</script>

<style scoped>
.container{
  position: relative;
  width: 300px;
  height: 250px;
  background-color: lightblue;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 0 0 5px 5px;
  overflow: auto;
  border:2px solid darkblue;
  border-top: none;
}

li{
  position: relative;
  left: 50%;
  transform: translateX(-50%);
  background-color: dodgerblue;
  width: 95%;
  padding: 10px;
  font-weight: bold;
  list-style: none;
  margin-top: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center; 
  color: white;
  transition: all 0.25s ease-in-out;
} 
.fa-trash-alt{
  color: crimson;
  cursor: pointer;
}

.fa-trash-alt:hover{
  color:red;
}

.fa-square{
  color: white;
  cursor: pointer;
  margin-left: 3px;
}


.fa-square-check{
  color: white;
  cursor: pointer;
  margin-left: 3px;
}

strong{
  position: absolute;
  padding: 10px 20px; 
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
  background-color: deeppink;
  box-shadow: 5px 5px 5px purple;
  font-size: 1.7rem;
  font-weight: bold;
  white-space: nowrap;
  border-radius: 5px;
}

#check{
  background-color:green;
  text-decoration: line-through;
}

#notCheck{
  background-color: dodgerblue;
  text-decoration: none;
}
</style>
