<template>
  <div class="add-card-wrapper">
    <h1 class="limit">
      ADD A NEW <br />
      BANK CARD
    </h1>

    <Card
      :name="cardName"
      :cardNumber="cardNumber"
      :vendor="getVendorImage"
      :cardStyle="setStyle"
      :year="chosenYear"
      :month="chosenMonth"
      :wifi="getVendorWifi" 

    />

    <div class="card-info">
      <article>
        <p>CARD NUMBER</p>
        <input
          type="text"
          v-model="cardNumber"
          placeholder="XXXX XXXX XXXX XXXX"
        />
      </article>

      <article>
        <p>CARDHOLDER NAME</p>
        <input
          type="text"
          v-model="cardName"
          placeholder="Firstname Lastname"
        />
      </article>

      <section class="dates">
        <article>
          <p>MONTH</p>
          <Dropdown :list="months" v-on:chosen-option="setMonth"  />
        </article>

        <article>
          <p>YEAR</p>
          <Dropdown :list="years" v-on:chosen-option="setYear" />
        </article>
      </section>

      <article>
        <Dropdown :list="vendor" @chosen-option="setVendor" />
      </article>

      <button @click="addToWallet"><h1>ADD CARD</h1> </button>
    </div>
  </div>
</template>



<script>
import Card from "../components/Card.vue";
import Dropdown from "../components/Dropdown.vue";
export default {
  computed: {
    getVendorImage() {
      let imgSrc = "";
      switch (this.chosenVendor) {
        case "Bitcoin inc":
          imgSrc = "bitcoin.svg";
          break;
        case "Ninja bank":
          imgSrc = "ninja.svg";
          break;
        case "Block chain inc":
          imgSrc = "blockchain.svg";
          break;
        case "Evil corp":
          imgSrc = "evil.svg";
          break;

        default:
          imgSrc = "bitcoin.svg";
          break;
      }
      return imgSrc;
    },
     getVendorWifi() {
      if(this.chosenVendor=="Bitcoin inc" || this.chosenVendor==""){
        return "wifi.svg"
      }
      else return "wifi_white.svg"
    },

    setStyle() {
      let cardStyle = {};
      switch (this.chosenVendor) {
        case "Bitcoin inc":
          cardStyle = {
            background: "linear-gradient(248.04deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0) 99.07%), #FFAE34",
            color: "black",
          };
          break;

        case "Ninja bank":
          cardStyle = {
            background: " linear-gradient(248.3deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0) 100%), #222222",
            color: "white",
          };
          break;

        case "Block chain inc":
          cardStyle = {
            background: "linear-gradient(248.52deg, rgba(0, 0, 0, 0.15) 1.49%, rgba(0, 0, 0, 0) 100%), #8B58F9",
            color: "white",
          };
          break;

        case "Evil corp":
          cardStyle = {
            background: " linear-gradient(248.3deg, rgba(0, 0, 0, 0.16) 0%, rgba(0, 0, 0, 0) 100%), #F33355",
            color: "white",
          };
          break;

        default:
            cardStyle={  
          background: "linear-gradient(248.3deg, rgba(255, 255, 255, 0.24) 0%, rgba(255, 255, 255, 0) 100%), #D0D0D0",
          color: "black"}
          break;
      }
      return cardStyle;
    },
  },

  components: { Card, Dropdown },
  data() {
    return {
      wifiSrc: "",
      cardName: "",
      cardNumber: "",
      vendor: ["Bitcoin inc", "Ninja bank", "Block chain inc", "Evil corp"],
      years: ["22", "23", "24", "25", "26", "27", "28", "29", "30"],
      months: [
        "01",
        "02",
        "03",
        "04",
        "05",
        "06",
        "07",
        "08",
        "09",
        "10",
        "11",
        "12",
      ],
      chosenVendor: "",
      chosenYear:"",
      chosenMonth:"",
    };
  },
  methods: {
    addToWallet(){   
    let card = {
      name:this.cardName,
      cardNumber:this.cardNumber,
      vendor:this.getVendorImage,
      cardStyle:this.setStyle,
      year:this.chosenYear,
      month:this.chosenMonth,
      wifi:this.getVendorWifi
    }
    this.$emit("card-submitted",card)

    },

    setVendor(item) {
      this.chosenVendor = item;
    },
    setYear(item){
      this.chosenYear=item;
    },
    setMonth(item){
      this.chosenMonth=item;
    },

  },
};
</script>

<style scoped>
.limit {
  text-align: center;
}
.add-card-wrapper > * {
  width: 82vw;
}
.card-info {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 15rem;
}
article {
  display: flex;
  flex-direction: column;
  margin-top: 1rem;
}
input {
  border-radius: 1px;
  height: 2.5rem;
}
.dates {
  display: flex;
  justify-content: space-between;
}
.dates > * {
  width: 47%;
}
p {
  padding: 0;
  margin: 0.3rem 0rem;
}
/* button {
  background-color: black;
  color: white;
  padding: 1.5rem 0rem;
  margin-top: 2rem;
  border-radius: 25px;
  border: 0;
  font-weight: 600;
  letter-spacing: 2px;
} */

</style>