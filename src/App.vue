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

  margin: 0;
  padding: 0;
}
</style>

