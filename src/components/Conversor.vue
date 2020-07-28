<template>
  <div class="conversor">
    <h2>{{ currencyA }} to {{ currencyB }}</h2>
    <form v-on:submit.prevent="converter">
      <input
        type="text"
        v-model="currencyA_value"
        v-bind:placeholder="currencyA"
      />
      <input
        height="100%"
        type="button"
        v-on:click.prevent="converter"
        value="Converter"
      />
    </form>
    <h2>
      {{ currencyB_value }}
    </h2>
  </div>
</template>

<script>
// import dotenv from "dotenv";

// dotenv.config({
//   path: process.env.NODE_ENV === "test" ? ".env.testing" : ".env",
// });

export default {
  name: "Conversor",
  props: ["currencyA", "currencyB"],
  data() {
    return {
      currencyA_value: "",
      currencyB_value: parseFloat(0).toFixed(2),
    };
  },
  methods: {
    converter() {
      const api_key = process.env.VUE_APP_CURRENCY_API_KEY;
      const de_para = `${this.currencyA}_${this.currencyB}`;

      const url =
        "https://free.currconv.com/api/v7/convert?q=" +
        de_para +
        "&compact=ultra&apiKey=" +
        api_key;

      fetch(url)
        .then((response) => response.json())
        .then((responseJson) => {
          const quotation = responseJson[de_para];
          this.currencyB_value = (
            parseFloat(this.currencyA_value) * quotation
          ).toFixed(2);
        });
    },
  },
};
</script>

<style scoped>
.conversor {
  width: 350px;
  height: 200px;

  display: flex;
  flex-direction: column;
  justify-content: center;

  border-radius: 10px;
  box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.1);

  padding: 5px 20px;
}
</style>
