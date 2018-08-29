<template>
  <div id="app">
    <img alt="Ron Image" src="./assets/ron.webp">
    <quote v-for='(quote, index) in ronsWisdom' v-bind:key='"quote"+index' v-bind:ronsWisdom='quote'/>
    <button v-on:click='getQuotes'>NEW QUOTE</button> 
  </div>
</template>

<script>
import quote from "./components/quote";

export default {
  name: "app",
  components: {
    quote
  },
  data() {
    return {
      ronsWisdom: null
    };
  },
  props: [],
  methods: {
    getQuotes() {
      fetch("http://ron-swanson-quotes.herokuapp.com/v2/quotes/")
        .then(resp => resp.json())
        .then(resp => (this.ronsWisdom = resp));
    }
  },
  mounted() {
    this.getQuotes();
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
  color: red;
  width: 10vw;
  height: 5vw;
  font-size: 15px;
}
</style>
