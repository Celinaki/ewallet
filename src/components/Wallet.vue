<template>
  <div>
    <h1>E-WALLET</h1>
   
    <Card
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
      activeCard: {},
      active: false,
    };
  },

  methods: {
    setActive(card) {
      console.log("klickad");
      console.log(card);
      this.activeCard = card;
      this.active = true;
    },
  },
};
</script>

<style scoped>
</style>