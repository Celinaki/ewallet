<template>
<div>
  <div v-on:click="setInfo">
    <div class="card-holder" :style="cardStyle">
      <div class="card-wrapper">
        <section class="card-top">
          <article class="chip-wifi">
            <img :src="require('../assets/' + wifi)" />

            <img src="../assets/chip.svg" />
          </article>
          <img :src="require('../assets/' + vendor)" class="vendor" />
        </section>
        <section class="card-number">
          <h1>{{ fourth }}</h1>
        </section>
        <section class="card-bottom">
          <article class="name-info">
            <p class="smallp">CARD HOLDER NAME</p>
            <p class="biggerp">{{ name }}</p>
          </article>
          <article class="valid">
            <p class="smallp">VALID THRU</p>
            <p class="biggerp">{{ formatDate }}</p>
          </article>
        </section>
      </div>
      </div>
    </div>
    </div>
</template>

<script>
export default {
  computed: {

    formatDate() {
      if(!this.month && !this.year ){
        return"MM/YY"
      }
      else if (!this.month && this.year){
        return "MM/"+this.year
      }
      else if(this.month && !this.year){
        return this.month + "/YY"
      }
      else return this.month + "/" + this.year;
    },

    fourth(){
      let computedCardNumber=""
      for(let i=0; i< this.cardNumber.length; i++){
        computedCardNumber+=this.cardNumber[i]
        if((i+1) % 4 == 0 ){
           computedCardNumber+=" "
      }
    }
return computedCardNumber
    },

  },
  mounted() {},
  props: {
    cardNumber: {
      type: String,
    },
    cardStyle: {
      type: Object,
    },
    name: String,
    month: String,
    year: String,
    vendor: {
      type: String,
      default: "bitcoin.svg",
    },
    wifi: {
      type: String,
    },
    chip: {
      type: String,
      default: "chip.svg",
    },
  },
  methods: {
setInfo() {
      let cardInfo = {
        name: this.name,
        cardNumber: this.cardNumber,
        vendor: this.vendor,
        cardStyle: this.cardStyle,
        year: this.year,
        month: this.month,
        wifi: this.wifi,
      };
      this.$emit("clicked", cardInfo);
    },
       
  },
  data() {
    return {

    };
  },
};
</script>


<style scoped>
.card-holder {
  width: 82vw;
  height: 12rem;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
  border-radius: 8px;
  align-self: center;
}
.card-wrapper {
  padding: 0.5rem;
}
.chip-wifi, .valid, .name-info {
  display: flex;
  flex-direction: column;
}
.chip-wifi > * {
  max-height: 1.8rem;
  margin-top: 2px;
}
.vendor {
  max-height: 2.8rem;
}
.card-top,
.card-bottom {
  display: flex;
  justify-content: space-between;
}
.card-bottom {
  margin-top: 2rem;
}
p {
  padding: 0;
  margin: 0;
}
h1 {
  text-align: center;
  font-size: 22px;
  letter-spacing: 1px;
  font-weight: 300;
}
.smallp {
  font-size: 10px;
  font-weight: 100;
}
.biggerp {
  font-size: 19px;
}
</style>