<template>
  <div class="calc">
    <div class="display">
      <input v-model.number="operand1" />
      <input v-model.number="operand2" />
      =
      <input readonly :value="result" />
      <!-- = {{ result }} -->
    </div>
    <div class="keyboard">
      <button
        v-for="operand in operands"
        v-bind:key="operand"
        v-bind:title="operand"
        @click="calculate(operand)"
        class="button_function"
      >
        {{ operand }}
      </button>
    </div>
    <div class="touch_input">
      <input type="radio" id="one" value="1" v-model="selectOperand" />
      <label for="one">Один</label>
      <input type="radio" id="two" value="2" v-model="selectOperand" />
      <label for="two">Два</label>
    </div>
    <div class="touch_keys">
      <button
        v-for="key_number in keys_numbers"
        v-bind:key="key_number"
        v-bind:title="key_number"
        @click="input(key_number)"
        class="touch_key"
      >
        {{ key_number }}
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "main_calc",
  data() {
    return {
      operands: ["+", "-", "*", "/", "Степень", "C"],
      keys_numbers: Array.from(Array(11).keys()),
      operand1: 0,
      operand2: 0,
      result: 0,
      selectOperand: "1",
    };
  },
  methods: {
    calculate(operation = "+") {
      this.error = "";

      switch (operation) {
        case "+":
          this.result = this.operand1 + this.operand2;
          break;
        case "-":
          this.result = this.operand1 - this.operand2;
          break;
        case "/":
          this.result = this.operand1 / this.operand2;
          break;
        case "*":
          this.result = this.operand1 * this.operand2;
          break;
        case "Степень":
          this.result = Math.pow(this.operand1, this.operand2);
          break;
        case "C":
          if (this.selectOperand == "1") {
            this.operand1 = this.operand1.toString().length > 1 ? parseInt(this.operand1.toString().slice(0, -1)) : 0;
          } else {
            this.operand2 = this.operand1.toString().length > 1 ? parseInt(this.operand2.toString().slice(0, -1)) : 0;
          }
          break;

        default:
          break;
      }
    },
    input(number){
      if (this.selectOperand == "1") {
        this.operand1 = parseInt(this.operand1.toString()+number)
      } else {
        this.operand2 = parseInt(this.operand2.toString()+number)
      }
    }
  },
};
</script>
<style scoped>
.display input {
  padding: 10px;
  margin: 10px;
  font-size: x-large;
  max-width: 100px;
  border: 0px solid grey;
  border-radius: 10px;
  box-shadow: 0px 0px 2px grey;
}
.button_function {
  min-width: 40px;
  height: 40px;
  margin: 5px;
  font-size: 20px;
  padding: 10px;
  border-radius: 40px;
  border: 1px black solid;
  background-color: white;
}

.touch_key {
  min-width: 40px;
  height: 40px;
  margin: 5px;
  font-size: 20px;
  padding: 10px;
  border-radius: 40px;
  border: 1px white;
  background-color: grey;
  color: white;
}

.keyboard {
  margin-top: 20px;
}

.calc {
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
