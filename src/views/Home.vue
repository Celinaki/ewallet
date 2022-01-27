<template>
    <div class="homewrap">
        <Wallet
        :cardList="cardList"
        />
        <button @click="addCard"><h1> ADD CARD</h1></button>
    </div>
</template>

<script>
import Wallet from '../components/Wallet.vue'
export default {

    props:{
        cardList:Array
    },
    components:{Wallet},
    data() {return{
       
    } },
    methods:{
            addCard(){
            this.$emit('add-card')
            console.log("Hej")
        }
    } 

}
</script>

<style >
.homewrap{
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
}
button{
  /* background-color: rgb(255, 255, 255);
  color: rgb(0, 0, 0);
  padding: 0.1rem 0rem;
  margin-top: 2rem;
  border-radius: 25px;
  border: 3px solid black;
  font-weight: 100;
  letter-spacing: 2px;
  min-width: 70vw; */
  }
</style>