<template>
        <div class="quantity-toggle">
        <button @click="decrement()">&mdash;</button>
        <input type="text" width="5" :value="quantity" readonly>
        <button @click="increment()">&#xff0b;</button>
        </div>
</template>

<script>
export default{
    name: 'quantity',
    data() {
        return {
            quantity: 1,
        }
    },
    methods: {
        increment (){
            this.quantity++
        },
        decrement (){
            if(this.quantity ===1){
                alert('Negative quantity not allowed')
            } else {
                this.quantity--
            }
        }
    }
  }
</script>

<style>
 input {
    border-top: $border;
    border-bottom: $border;
    width: 2.0rem;
    text-align: center;
    padding: 0 .5rem;
  }
</style>