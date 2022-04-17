<template>
  <div class="calc">
    <div class="display">
      <input v-model="operand1" />
      <input v-model="operand2" />
      = 
      <input readonly :value="result" />
      <!-- = {{ result }} -->
    </div>
    <div class="keyboard">
      <button @click="result = +operand1 + +operand2">+</button>
      <button @click="result = +operand1 - +operand2">-</button>
      <button @click="result = +operand1 / +operand2">/</button>
      <button @click="result = +operand1 * +operand2">*</button>
      <button @click="result = Math.pow(+operand1, +operand2)">&#176;</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "main_calc",
  data() {
    return {
      operand1: 0,
      operand2: 0,
      result: 0,
    };
  },
};
</script>
<style scoped>
input {
    padding: 10px;
    margin: 10px;
    font-size: x-large;
    width: 60px;
}
button {
    width: 40px;
    height: 40px;
    margin: 5px;
    font-size: 20px;
    padding: 10px;
    border-radius: 40px;
    border: 1px black solid;
    background-color: white;
}
.keyboard {
    margin-top: 20px;
}

.calc, input {
    border: 0px solid grey;
    border-radius: 10px;
    box-shadow: 0px 0px 2px grey;
}

.calc {
    display: flex;
    justify-content: center;
    flex-direction: column;
    background-color: white;
    max-width: -webkit-max-content;
    max-width: -moz-max-content;
    max-width: max-content;
    margin-left: auto;
    margin-right: auto;
    padding: 20px;
}
</style>
