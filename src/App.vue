<template>
  <div id="container">
    <h1 style="textAlign:left;">Grocery Simulator</h1>
    <form id="app" @submit.prevent="change">
    <label><strong> Milk: ${{milk.price.toFixed(2)}} &nbsp;</strong></label> 
    <input v-model.number="milk.quantity" width="5">
    <br>
    <button @click="addToCart(milk)">Add To Cart</button>
    <br><br>
    <label><strong> Eggs: ${{eggs.price.toFixed(2)}} &nbsp;</strong></label> 
    <input v-model.number="eggs.quantity" width="5">
    <br>
    <button @click="addToCart(eggs)">Add To Cart</button>
     <br><br>
    <label><strong> Bread: ${{bread.price.toFixed(2)}} &nbsp;</strong></label> 
    <input v-model.number="bread.quantity" width="5">
    <br>
    <button @click="addToCart(bread)">Add To Cart</button>
     <br><br>
    <label><strong> Peanut Butter: ${{peanutbutter.price.toFixed(2)}} &nbsp;</strong></label> 
    <input v-model.number="peanutbutter.quantity" width="5">
    <br>
    <button @click="addToCart(peanutbutter)">Add To Cart</button>
     <br><br>
    <label><strong> Jelly: ${{jelly.price.toFixed(2)}} &nbsp;</strong></label> 
    <input v-model.number="jelly.quantity" width="5">
    <br>
    <button @click="addToCart(jelly)">Add To Cart</button>
    <br><br>
    <label><strong> Lemonade: ${{lemonade.price.toFixed(2)}} &nbsp;</strong></label> 
    <input v-model.number="lemonade.quantity" width="5">
    <br>
    <button @click="addToCart(lemonade)">Add To Cart</button>
    <br><br>
    <label><strong> Pizza: ${{pizza.price.toFixed(2)}} &nbsp;</strong></label> 
    <input v-model.number="pizza.quantity" width="5">
    <br>
    <button @click="addToCart(pizza)">Add To Cart</button>
    <br><br>
    <label><strong> Donuts: ${{donuts.price.toFixed(2)}} &nbsp;</strong></label> 
    <input v-model.number="donuts.quantity" width="5">
    <br>
    <button @click="addToCart(donuts)">Add To Cart</button>
    <br><br>
    <label><strong> Pineapple: ${{pineapple.price.toFixed(2)}} &nbsp;</strong></label> 
    <input v-model.number="pineapple.quantity" width="5">
    <br>
    <button @click="addToCart(pineapple)">Add To Cart</button>
    <br><br>
    <label><strong> Chicken: ${{chicken.price.toFixed(2)}} &nbsp;</strong></label> 
    <input v-model.number="chicken.quantity" width="5">
    <br>
    <button @click="addToCart(chicken)">Add To Cart</button>
    </form>
    
    <form id="cart" @submit.prevent="change">
    <h1>Shopping Cart:</h1>
    <li v-for="item in cart" v-bind:key="item.id">
      {{item.name}}&nbsp;({{item.quantity}}x):&nbsp;${{item.subtotal.toFixed(2)}}
    </li>
    <br>
    <label><strong>Subtotal:&nbsp;${{total.toFixed(2)}}</strong></label>
    </form>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      cart:[],
      recordID:[],
      total: 0,
      milk:{
        id: 1,
        name: "Milk",
        price: 2.99,
        quantity: 1
      },
      eggs:{
        id: 2,
        name: "Eggs",
        price: 3.99,
        quantity: 1
      },
       bread:{
        id: 3,
        name: "Bread",
        price: 2.25,
        quantity: 1
      },
       peanutbutter:{
        id: 4,
        name: "Peanut Butter",
        price: 4.25,
        quantity: 1
      },
       jelly:{
        id: 5,
        name: "Jelly",
        price: 3.50,
        quantity: 1
      },
      lemonade:{
        id: 6,
        name: "Lemonade",
        price: 4.50,
        quantity: 1
      },
      pizza:{
        id: 7,
        name: "Pizza",
        price: 4.99,
        quantity: 1
      },
      donuts:{
        id: 8,
        name: "Donuts",
        price: 2.99,
        quantity: 1
      },
      pineapple:{
        id: 9,
        name: "Pineapple",
        price: 1.99,
        quantity: 1
      },
      chicken:{
        id: 10,
        name: "Chicken",
        price: 2.60,
        quantity: 1
      },
  }
  },
  methods:{
    addToCart(item){
      if(this.recordID.includes(item.id)){
        this.cart.map((x) => {
          if(x.id == item.id){
            x.subtotal = x.subtotal + (item.price * item.quantity)
            x.quantity = x.quantity + item.quantity
          }
        });
      }else{
      this.cart.push({id: item.id, name: item.name, subtotal: item.price * item.quantity, quantity: item.quantity})
      this.recordID.push(item.id)
      }
      this.total = 0
      this.cart.map((x) => {
        this.total = this.total + x.subtotal
      });
    }
   }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 40px;
  float: left;
},
#container{
  display: flex;
  align-items: center;
  justify-content: center
},
#cart{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: right;
  color: #2c3e50;
  margin-top: 60px;
  float: right;
}
</style>
