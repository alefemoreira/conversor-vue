<template>
  <div id="app">
    <header>
      <img alt="Vue logo" height="100px" src="./assets/logo.png" />
      <h1>Conversor de Moedas com Vue.js</h1>
    </header>

    <div class="row">
      <Conversor currency-a="USD" currency-b="BRL" />
      <Conversor currency-a="BRL" currency-b="USD" />
    </div>
    <div class="row">
      <Conversor currency-a="CAD" currency-b="BRL" />
      <Conversor currency-a="BRL" currency-b="CAD" />
    </div>
    <div class="row">
      <Conversor currency-a="EUR" currency-b="BRL" />
      <Conversor currency-a="BRL" currency-b="EUR" />
    </div>
    <div class="row">
      <Conversor currency-a="GBP" currency-b="BRL" />
      <Conversor currency-a="BRL" currency-b="GBP" />
    </div>
  </div>
</template>

<script>
import Conversor from "./components/Conversor.vue";

export default {
  name: "App",
  components: {
    Conversor,
  },
};
</script>

<style>
#app {
  width: 900px;
  margin: auto;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center;   */
  color: #2c3e50;
  margin-top: 60px;
  margin-bottom: 60px;
}

#app header {
  display: flex;
  justify-content: center;
}

#app header img {
  margin-right: 30px;
}

#app .row {
  display: flex;
  justify-content: space-around;

  margin-top: 24px;
}
</style>
