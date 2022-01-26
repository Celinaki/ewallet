<template>
  <div>
    <h1>E-WALLET</h1>
    <Card
    v-if="active"
   
    :cardNumber="this.activeCard.cardNumber"
    :cardStyle="this.activeCard.cardStyle"
    :vendor="this.activeCard.vendor"
    :wifi="this.activeCard.wifi"
    :chip="this.activeCard.chip"
    :name="this.activeCard.name"
    :year="this.activeCard.year"
    :month="this.activeCard.month"
    />
<div class="card-box">
    <Card
     @clicked="setActive(card)"
      v-for="(card, index) in cardList"
      :key="index"
      :name="card.name"
      :cardNumber="card.cardNumber"
      :vendor="card.vendor"
      :cardStyle="card.cardStyle"
      :year="card.year"
      :month="card.month"
      :wifi="card.wifi"  
    />
</div>

  </div>
</template>

<script>
import Card from "../components/Card.vue";
export default {
  components: {
    Card,
  },
  props: {
    cardList: {
      type: Array,
    },
  },
  data() {
    return {
      activeCard:{},
      active:false,

    };
  },

  methods: {
    setActive(card){
      console.log("klickad")
      this.activeCard= card;
      this.active=true

    }
  },
};
</script>

<style scoped>
.card-box{
  position: relative;
  margin-top:-100px;
}
</style>