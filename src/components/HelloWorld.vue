<template>
  <div>
    <div>{{ message }}</div>
    <input v-model="message">
    <button v-on:click="reverseMessage">Inverter Mensagem</button>
    <ul>
      <li v-for="(product, i) in products" :key="i">
        <span>{{ product.name }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "Primeiros Passos Vue",
      products: []
    };
  },
  created() {
    fetch("http://www.mocky.io/v2/5cf15226300000116e00be51")
      .then(response => response.json())
      .then(json => {
        this.products = json.products;
      });
  },
  methods:{
    reverseMessage: function(){
      this.message = this.message.split('').reverse().join('')
    }
  }
};
</script>

<style>
li{
  text-align: left;
  list-style: none;
}
</style>