<template>
 <div>
 <div>
    <div>
      <!-- <Burger v-for="burger in burgers"
              v-bind:burger="burger" 
              v-bind:key="burger.name"/> -->

  </div>
  </div>
  <header id="header">
    <img src= "https://res.cloudinary.com/tf-lab/image/upload/w_600,h_337,c_fill,q_auto,f_auto/restaurant/73d6d3da-fbae-4b4f-af5b-4b14c68bf3ee/4f0a9d3e-3766-4923-98eb-49d17c87a734.jpg" id = "headerpicture">
    <h1 id="headertext">Välkommen till BurgerOnline</h1>
    </header>

   <main>
   <div class ="wrapper">
   <h1 class="burgerselection"> Burger selection</h1>

      <!-- <div class="box oxburgare">
      <h1>Oxburgare</h1>
      <p>
      <img src="https://imageproxy.wolt.com/menu/menu-images/5f8012022b0d9c9eda6a2e65/fb80990e-21d1-11ec-a702-de3e1444ebfb_cheese_burger.jpeg" alt="Ox" title = "Ox" style ="width: 200px" height = "200">
      </p>

      <ul>
      <section class = "ingredients">
    
    
    <span id="in"><li>Veganfri</li></span>
    <span id="in"><li>100% Söggel</li></span>
    <span id="in"><li>Glutenfri</li></span>
    
    </section>
    </ul>
    </div>
      
      <div class = "box ostburgare">
      <h1>Ostburgare</h1>
      <p>
      <img src = "https://s23209.pcdn.co/wp-content/uploads/2022/07/220602_DD_The-Best-Ever-Cheeseburger_267-1200x1200-cropped.jpg" alt= "ost" title = "ost" style = "width: 200px">
      </p>
      

      <ul>
      <section class = "ingredients">
    
     <span id="in"><li>Laktos</li></span>
     <span id="in"><li>Lök</li></span>
     <span id="in"><li>Gluten</li></span>
    
    </section>
</ul>
    </div>

    
    <div class = "box diverseburgare" >
    
      <h1>Diverseburgare</h1>
      <p>
      <img src = "https://img.cdn4dd.com/p/fit=cover,width=1200,height=1200,format=auto,quality=50/media/photos/d5e92442-6aa8-4e0e-ba11-02df8c201503-retina-large.jpg" alt="diverse" title = "diverse" style= "width: 200px">
      </p>
  

      <ul>
    <section class = "ingredients">
     <span id="in"><li>Köttmängd okänt</li></span>
     <span id="in"><li>Innehåller alkohol</li></span>
     <span id="in"><li>Legaliteten kontrollerad</li></span>
    </section>
</ul>

</div> -->
<Burger v-for="burger in burgers"
        v-bind:burger="burger" 
        v-bind:key="burger.name"
        v-on:orderedBurger="addToOrder($event)"/>






</div>

    
      <div id="contact">

         <h1>Customer information</h1>
         <form>
         <p>
    <label for="firstname">Full name</label><br>
    <input type="text" id="firstname" v-model="fn" required="required" placeholder="First- and Last name">
</p>

<p>
    <label for ="E-mail">E-mail</label><br>
    <input type="email" id="email" v-model="em" required="required" placeholder="E-mail address">
</p>
<!-- <p>
<label for = "Street">Street</label><br>
<input type = "text" id ="street" v-model="st" required = "required" placeholder="Street Name">
</p>
<p>
<label for = "House">House</label><br>
<input type = "number" id ="house" v-model="hs" required = "required" placeholder="House number">
</p> -->
<p>
   <label for="payment">Payment methods</label><br>
   <select id="payment" name="payment" v-model="gibs">
       <option>Credit Card</option>
       <option>Cash by mail</option>
       <option>Swish</option>
       <option selected="true">Bitcoin</option>
       <option>Invoice</option> 
   </select>
   </p>
   <p>
   <label for = "gender"> Select Gender </label><br>
<input type="radio" id="man" v-model="gender" value="Man" checked>
<label for="man">Man</label><br>
<input type="radio" id="woman" v-model="gender" value="Woman">
<label for="woman">Woman</label><br>
<input type="radio" id="javascript" v-model="gender" value="Unknown">
<label for="not telling">Do not wish to tell</label> 
</p>
         </form>
    
         </div>
         <div id="maparea">
          <div id="map" v-on:click="setLocation">
            <div id="dots" v-bind:style="{position:absolute}">
              <div id="dots div" v-bind:style="{ left:location.x + 'px', 
                      top: location.y + 'px' }">
                      
    T
</div>
</div>
          
          
    

         
          </div>
          </div>



      <button v-on:click="addOrder" type="submit" class="button">
  <img src="https://image.shutterstock.com/image-vector/green-shiny-button-metallic-elements-260nw-125207996.jpg" style = "width:50px">
  Send Order!
</button>


   </main>
   <hr>
   <footer>
     By Erik Magnusson, all rights reserved
   </footer>

   
</div>
</template>

<script>
import Burger from '../components/OneBurger.vue'
import io from 'socket.io-client'
import menu from '../assets/menu.json'

const socket = io();

// function MenuItem(name,kCal,img,lactose,gluten){
//   this.name = name;
//   this.img = img;
//   this.kCal = kCal,
//   this.gluten = gluten;
//   this.lactose = lactose;
// }

// let oxburgare = new MenuItem("Oxburgare",500,"https://imageproxy.wolt.com/menu/menu-images/5f8012022b0d9c9eda6a2e65/fb80990e-21d1-11ec-a702-de3e1444ebfb_cheese_burger.jpeg",true,false);
// let ostburgare = new MenuItem("Ostburgare",850,"https://s23209.pcdn.co/wp-content/uploads/2022/07/220602_DD_The-Best-Ever-Cheeseburger_267-1200x1200-cropped.jpg",false,true);
// let diverseburgare = new MenuItem('Diverseburgare',700,"https://img.cdn4dd.com/p/fit=cover,width=1200,height=1200,format=auto,quality=50/media/photos/d5e92442-6aa8-4e0e-ba11-02df8c201503-retina-large.jpg",true,true);
// console.log(oxburgare);
// console.log(ostburgare);
// console.log(diverseburgare);

let burgerarray = menu;
 
// console.log(burgerarray);


export default {
  name: 'HomeView',
  components: {
    Burger
  },
  data: function () {
    return {
      burgers:menu,
      fn:'',
      em:'',
      gibs:"Bitcoin",
      gender:'Man',
      orderedBurgers:{},
      location: { x:0,
                  y:0
                
                },
      // orders:null,
          

}
  },
  


 
  methods: {
    getOrderNumber: function () {
      return Math.floor(Math.random()*100000);
    },

    setLocation:function(event){
      var offset = {x: event.currentTarget.getBoundingClientRect().left,
                    y: event.currentTarget.getBoundingClientRect().top};


      this.location.x = event.clientX - 10 - offset.x;
      this.location.y = event.clientY - 10 - offset.y;



    },
    addOrder: function () {


              
    socket.emit( "addOrder", { orderId: this.getOrderNumber(),
                                details: { x: this.location.x,
                                           y: this.location.y, 
                                           firstname:this.fn,
                                           email:this.em,
                                           payment:this.gibs,
                                           gender: this.gender},
                                orderItems: this.orderedBurgers
                                
                            
          

                              
                                

                                
                              } 
                 );
                console.log(this.orderedBurgers);
                console.log(orderItems);
    },

    addToOrder: function (event) {
      this.orderedBurgers[event.name] = event.amount;
      console.log(this.orderedBurgers);
    },

    // clearQueue: function () {
    //     socket.emit('clearQueue');
    //   }

}
  }


</script>

<style>
body {
    font-family: arial;
 }

 .burgerselection{
   position: absolute;
   margin-top:-15px;
   padding:20px;
   margin-bottom:15px;
   margin-left:-5px;
 }


.wrapper{
    display:grid;
    grid-gap:80px;
    grid-template-columns: 200px 200px 200px;
    background-color:black;
    color: white;
    border: 3px dashed white;
    padding:30px;
    margin:10px;
    margin-top:20px;

}

.box{
    background-color:black;
    color: white;
    padding: 20px;
    margin: 10px; 
    border-radius:10px;
    margin-top: 20px;

}

#header{
    background-color: white;
    color:black;
    padding: 10px;
    margin: 5px;
    height: 200px;
    overflow:hidden;
}

#headertext{
    position:absolute;
    margin-top:-750px;
    margin-left:40px;
}

 #headerpicture{
    height: auto;
    width:100%;
    margin-left:0px;
    position:left;
    opacity:0.8;
    overflow:hidden;

 }
 

 .ingredients{
    color: #ff5500;
    margin-left:-20px;

 }
 
 #in {
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    
 }

 #contact {
    background-color: white;
    color:black;
    border: 3px dashed black;
    padding: 10px;
    margin: 10px;
 }
 
 #burgers{
    background-color:black;
    color: white;
    border:3px dashed white;
    padding: 10px;
    margin: 10px;
 }

 .button{
    padding-left:20px;
    margin:10px;
 }

 .button:hover{
    background-color:#002ead;
    transition: 0.7s;

 }

#burgerstyle{
    display:inline-block;
    padding:20px;
    margin-left:50px;
   
}

#dots {
    position: relative;
    margin: 0;
    padding: 0;
    background-repeat: no-repeat;
    width:1920px;
    height: 1078px;
    cursor: crosshair;
  }

  #dots div {
    position: absolute;
    background: black;
    color: white;
    border-radius: 10px;
    width:20px;
    height:20px;
    text-align: center;
  }



 /* .oxburgare{
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

 } */
  #map {

    height:1078px;
    width: 1920px;
    background: url('../../public/img/polacks.jpg');
  }

  #maparea{
  
    height:400px;
    width: auto;
    overflow:scroll;
    margin-left: 15px;
    
  }
</style>