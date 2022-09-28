

<template>
  <header class="header">
   <div class="logo">Logo</div>
    <div class="rightSide">
      <ul class="navList">
        <li v-for="link in links" class="linkItem">
          <a :href="link" >{{link.name}}</a>
          <div :class="[link.dropDown ? 'flex' : 'hidden' ]"  class="dropDown">
              {{link.dropDown && "dropdown"}}
          </div>
        </li>
      </ul>
      <div class="langue">
        <div class="langueTop" @click="dropDownOpen()"  >{{selectedLang==="" ?  "icon" : selectedLang}}</div>
        <ul :class="[open ? 'opened langueBottom' : 'langueBottom']">
          <li v-for="langue in langues" @click="selectLang(langue.name)" class="langueBottomItem">{{langue.name}}</li>
        </ul>
      </div>
      <Button>Get started</Button>
    </div>
  </header>
</template>
<script >
  import { ref } from "vue";
import Button from "./Button.vue"
  export default {
   
     setup() {
      let open=ref(false)
      let selectedLang=ref("")
    let links=[
      {
        name:"home",
        link:"#",
      },
      {
        name:"services",
        link:"#",
      },{
        name:"about",
        link:"#",
      },{
        name:"blog's",
        link:"#",
        dropDown:[""]
      },{
        name:"contact",
        link:"#",
      }
    ]
    let langues=[
      {
        name:"Français",
        drapeau:""
      },{
        name:"Anglais",
        drapeau:""
      },
      {
        name:"Arabe",
        drapeau:""
      },
    ]
    function dropDownOpen(){
      open.value= !open.value
    }
    function selectLang(id){
      console.log(id)
      selectedLang.value= id
    }
    return {links,open,dropDownOpen,selectedLang,selectLang,langues};
  },
   components:{
      Button
    }
  }
 
    
  
</script>
<style scoped>
  
  header{
    width: 100%;
    height: 80px;
    position: fixed;
    top: 0;
    left: 0;
    background-color: crimson;
    display: flex;
    align-items: center;
    justify-content: space-between;
    color: white;
    padding: 0 50px;
  }
  .logo{
    width: 50%;

  }
  .rightSide{
    width: 50%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  ul{
    list-style: none;
  }
  .navList{
    display: flex;
    align-items: center;
    gap: 20px;
    
  }
  .navList a{
    color: white;

  }
  .navList a:hover{
    color: darkblue;
    background-color: transparent;
  }
  .langue{
    position: relative;
  }
  .langueTop{
    cursor: pointer;
  }
  .langueBottom{
    position: absolute;
    background-color: chocolate;
    padding: 10px 15px;
    left: 50%;
    transform: translateX(-50%);
    top: 62px;
    display: flex;
    opacity: 0;
    pointer-events: none;
    flex-direction: column;
    gap: 3px;
  }
  .langueBottom.opened{
    top: 52px;
    transition:top .5s ease;
    opacity: 1;
    pointer-events: all;
  }
  .langueBottomItem{
    cursor: pointer;
  }
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
