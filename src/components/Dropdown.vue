<template >
    <div>   
        <div class="dropdown-placeholder" v-on:click="click=!click">
            <i class="fas fa-caret-down"></i>

      <ul v-if="click">
           <li v-for="(item, index) in list" :key="index" v-on:click="onClick(item)">
               {{item}}
           </li> 
        </ul>
        </div>
  

    </div>
</template>

<script>

export default ({
    props:{
        list:Array,
    },
    data() {return{
    click:false,
    }
    
        
    },
    methods:{
        onClick(item){

            this.$emit('chosen-vendor',item)
        
        }
    }
})
</script>

<style scoped>
.fas{
    margin: 1rem;
}
.dropdown-placeholder{
    display: flex;
    justify-content: flex-end;
    align-items: center;
    position: relative;
    border: 1px solid black;
    width:100%;
}
div>*{
    max-width:84vw ;
}
ul{
    border: 1px solid black;
    padding: 0;
    position: absolute;
    top: 0;
    width: 99.5%;  
    justify-self: center;
      background-color: rgb(228, 228, 228);
      overflow: scroll;
      max-height: 10rem;
      opacity: 1;
      z-index: 9000;


}
li{
    list-style-type: none;
    border-bottom: 1px solid rgb(87, 86, 86);
    padding: 0.8rem;

}
</style>
