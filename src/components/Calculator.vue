<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <table id="calculator" class="calculator">
      <tr>
        <td colspan="4">
          <h1 class="display-box" id="result">{{ input }}</h1>
        </td>
      </tr>
      <tr>
        <td colspan="4">
          <h1 class="" id="result">{{ message }}</h1>
        </td>
      </tr>
      <div>
        <tr>
          <td>
            <input
              class="buttons func-button"
              type="button"
              value="("
              v-on:click="$display('(')"
            />
          </td>
          <td>
            <input
              class="buttons func-button"
              type="button"
              value=")"
              v-on:click="$display(')')"
            />
          </td>
          <td>
            <input
              class="buttons func-button"
              type="button"
              value="CLR"
              v-on:click="input = ''"
              style="background-color: #e74c3c"
            />
          </td>
          <td>
            <input
              class="buttons func-button"
              type="button"
              value="DEL"
              v-on:click="input = input.substr(0, input.length - 1)"
              style="background-color: lightcoral"
            />
          </td>
        </tr>
        <tr>
          <td>
            <input
              class="buttons num-button"
              type="button"
              value="7"
              v-on:click="$display('7')"
            />
          </td>
          <td>
            <input
              class="buttons num-button"
              type="button"
              value="8"
              v-on:click="$display('8')"
            />
          </td>
          <td>
            <input
              class="buttons num-button"
              type="button"
              value="9"
              v-on:click="$display('9')"
            />
          </td>
          <td>
            <input
              class="buttons func-button"
              type="button"
              value="/"
              v-on:click="$display('/')"
            />
          </td>
        </tr>
        <tr>
          <td>
            <input
              class="buttons num-button"
              type="button"
              value="4"
              v-on:click="$display('4')"
            />
          </td>
          <td>
            <input
              class="buttons num-button"
              type="button"
              value="5"
              v-on:click="$display('5')"
            />
          </td>
          <td>
            <input
              class="buttons num-button"
              type="button"
              value="6"
              v-on:click="$display('6')"
            />
          </td>
          <td>
            <input
              class="buttons func-button"
              type="button"
              value="*"
              v-on:click="$display('*')"
            />
          </td>
        </tr>
        <tr>
          <td>
            <input
              class="buttons num-button"
              type="button"
              value="1"
              v-on:click="$display('1')"
            />
          </td>
          <td>
            <input
              class="buttons num-button"
              type="button"
              value="2"
              v-on:click="$display('2')"
            />
          </td>
          <td>
            <input
              class="buttons num-button"
              type="button"
              value="3"
              v-on:click="$display('3')"
            />
          </td>
          <td>
            <input
              class="buttons func-button"
              type="button"
              value="-"
              v-on:click="$display('-')"
            />
          </td>
        </tr>
        <tr>
          <td>
            <input
              class="buttons func-button"
              type="button"
              value="."
              v-on:click="$display('.')"
            />
          </td>
          <td>
            <input
              class="buttons num-button"
              type="button"
              value="0"
              v-on:click="$display('0')"
            />
          </td>
          <td>
            <input
              class="buttons func-button"
              type="button"
              value="="
              v-on:click="$calculate()"
              style="background-color: cyan"
            />
          </td>
          <td>
            <input
              class="buttons func-button"
              type="button"
              value="+"
              v-on:click="$display('+')"
            />
          </td>
        </tr>
      </div>
    </table>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      msg: "Welcome to CalculatorVue App",
      input: "",
      preButon: "",
      message: "",
    };
  },
  methods: {
    $eval(input) {
      console.log(input);
      return new Function("return " + input)();
    },
    $calculate() {
      try {
        this.preButon = "=";
        this.input = new Function("return " + this.input)();
      } catch (error) {
        this.message = "Something is wrong!";
      }
    },
    $display(value) {
      this.message = "";
      if (this.preButon == "=") this.input = "";
      this.input += value;
      this.preButon = "";
    },
  },
};
</script>

<style scoped>
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.calculator {
  width: 500px;
  height: auto;
  border-radius: 10px;
  padding: 10px;
  margin: auto;
  background-color: lightyellow;
  box-shadow: gainsboro;
}

.display-box {
  font-family: Arial;
  width: 92%;
  height: 50px;
  font-size: 30px;
  border-radius: 10px;
  margin: 8px;
  padding: 8px;
  border: 2px solid;
  color: darkcyan;
  text-align: right;
  vertical-align: bottom;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  font-family: sans-serif;
  width: 100px;
  height: 40px;
  font-size: larger;
  padding: 5px;
  margin: auto;
}

.func-button {
  background-color: bisque;
  border-color: bisque;
  border-radius: 8px;
}

.num-button {
  background-color: lavender;
  border-color: lavender;
  border-radius: 8px;
}

.func-button:hover {
  opacity: 60%;
}

.num-button:hover {
  opacity: 60%;
}
</style>
