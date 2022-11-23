<template>
    <!-- <div >
      {{ burger.name }} {{ burger.kCal }} {{burger.lactose}} {{burger.gluten}} 
    </div> -->
    <div class="box">
      <h1>{{ burger.name }}</h1>
      <p>
      <img class="burgerimage" v-bind:src="burger.img">
      </p>

      
      <ul>
      <section class = "ingredients">
        <span>
          <p>
            {{burger.kCal}} Kalorier
          </p>
          <p v-if="burger.lactose"> Innehåller <b>Laktos</b></p>
          <p v-if="burger.gluten"> Innehåller <b>Gluten</b></p>
          <button v-on:click="addBurger">+</button>
           Antal:{{amountOrdered}}
           <button v-on:click="amountOrdered -= 1">-</button>
          
        </span>
  
        
    
<!-- 
    <span id="in"><li>Veganfri</li></span>
    <span id="in"><li>100% Söggel</li></span>
    <span id="in"><li>Glutenfri</li></span> -->
    
    </section>
    </ul>
    </div>
    </template>
    
  <script>
  export default {
    name: 'OneBurger',
    props: {
      burger: Object
    },

    data:function(){

      return{
        amountOrdered:0,
      }
    },
methods:{
    addBurger: function () {
  this.amountOrdered += 1;
  this.$emit('orderedBurger', { name:   this.burger.name, 
                                amount: this.amountOrdered 
                              }
  );
                            }
},

  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
.box{
    background-color:black;
    color: white;
    padding: 10px;
    margin: 5px; 
    border-radius:10px;
    margin-top: 40px;


}

.burgerimage{
  width:200px;
  height:200px;
}

.ingredients{
    color: #e7dcd7;
    margin-left:-20px;

 }

 #in {
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    
 }

  
 .oxburgare{
    grid-column: 1;
    grid-row: 1/ span 3;

 }

 .ostburgare{
   grid-column: 2;
   grid-row: 1 / span 3;
    
 }

 .diverseburgare{
   grid-column: 3;
   grid-row : 1/ span 3;
 } 


 
  </style>
  