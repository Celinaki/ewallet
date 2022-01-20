<template>
    <div>
        <Wallet/>
        <button @click="addCard">Add Card</button>
    </div>
</template>

<script>
import Wallet from '../components/Wallet.vue'
export default {
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

<style scoped>

</style>