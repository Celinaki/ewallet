<template>
  <div id="app">
    <div class="wrapper">
      <Home v-if="currentView == 'home'" @add-card="toggleCurrentView"
      :cardList="cardList"

       />
      <AddCard v-else-if="currentView =='addCard'" v-on:card-submitted="addCardToWallet"/>
    </div>
  </div>
</template>

<script>
import Home from './views/Home.vue'
import AddCard from './views/AddCard.vue'

export default {
  components:{Home,AddCard},

  
  data() {return{
    currentView:'home',
    cardList:[]
  }},

  methods:{
    toggleCurrentView(){
      this.currentView='addCard'
      console.log("hej")
    },
    addCardToWallet(card){
      this.cardList.push(card)
      this.currentView='home'
    }
  }
}
</script>

<style >

h1{
  font-family: 'Source Sans Pro', sans-serif;;
}
p{
  font-family: 'PT Mono', monospace;

}
.wrapper{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
body,html{
  text-align: center;
  margin: 0;
  padding: 0;
}
button{
    background-color: rgb(255, 255, 255);
  color: rgb(0, 0, 0);
  padding: 0.5rem 0rem;
  margin-top: 2rem;
  border-radius: 20px;
  border: 3px solid black;
  font-weight: 100;
  letter-spacing: 2px;
  transition: 500ms;
  min-width:82vw ;
}
button:hover{
    transition: 500ms;

  background-color: black;
  color: white;
}
button>h1{
  margin:0
}
</style>

