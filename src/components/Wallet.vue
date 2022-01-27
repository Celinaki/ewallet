<template>
  <div>
    <h1>E-WALLET</h1>
    <Card
    v-if="active"
    class="active-margin"
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
      class="card-margin"
      v-for="(card, index) in cardList" 
      :key="index"
      :name="card.name"
      :cardNumber="card.cardNumber"
      :vendor="card.vendor"
      :cardStyle="card.cardStyle"
      :year="card.year"
      :month="card.month"
      :wifi="card.wifi"
      @clicked="setActive(card)"
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
      console.log("card")
      this.activeCard= card;
      this.active=true

    }
  },
};
</script>

<style scoped>


.active-margin{
  margin-top: 80px;
}
.card-box{
  align-self: center;
  margin-top: 150px;
  margin-bottom: 150px;
}
.card-box>*{
  position: relative;
  margin-top:-100px;
}
</style>