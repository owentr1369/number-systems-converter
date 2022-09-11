<template>
  <div class="home">
    <input type="text" placeholder="Enter your number" v-model="inputNumber" />
    <div>
      <label for="fromInput">FROM</label>
      <select name="" id="fromInput" v-model="inputFormat">
        <option
          :value="numberSystem.value"
          v-for="numberSystem in numberSystems"
          v-bind:key="numberSystem.id"
        >
          {{ numberSystem.title }}
        </option>
      </select>
    </div>
    <div>
      <label for="toInput">TO</label>
      <select name="" id="toInput" v-model="outputFormat">
        <option
          :value="numberSystem.value"
          v-for="numberSystem in numberSystems"
          v-bind:key="numberSystem.id"
        >
          {{ numberSystem.title }}
        </option>
      </select>
    </div>
    <div class="buttons">
      <button
        class="convert"
        @click="convert(inputFormat, outputFormat, inputNumber)"
      >
        Convert
      </button>
      <button class="clear" @click="clearInput('')">Clear</button>
    </div>
    <div class="output">
      <h1>{{ outputNumber.toString().toUpperCase() }}</h1>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

// types
import NumberSystem from "../types/NumberSystem";
import InputNumber from "../types/InputNumber";

export default defineComponent({
  name: "HomeView",
  setup() {
    const inputNumber = ref<InputNumber>("");
    const outputNumber = ref<InputNumber>("");

    const numberSystems = ref<NumberSystem[]>([
      { title: "Binary", value: "binary", id: "1" },
      { title: "Decimal", value: "decimal", id: "2" },
      { title: "Octal", value: "octal", id: "3" },
      { title: "Hexadecimal", value: "hexadecimal", id: "4" },
    ]);

    const clearInput = (input: string) => {
      inputNumber.value = input;
    };

    const inputFormat = ref<string>("decimal");
    const outputFormat = ref<string>("binary");

    // Decimal to orthers
    // 1. decimal to binary
    const decToBin = (input: InputNumber) => {
      console.log(Number(input).toString(2));
      outputNumber.value = Number(input).toString(2);
    };
    // 2. decimal to octal
    const decToOct = (input: InputNumber) => {
      outputNumber.value = Number(input).toString(8);
    };
    // 3. decimal to hex
    const decToHex = (input: InputNumber) => {
      outputNumber.value = Number(input).toString(16);
    };

    // Binary to orthers
    // 1. binary to decimal
    const binToDec = (input: InputNumber) => {
      outputNumber.value = parseInt(input.toString(), 2);
    };
    // 2. binary to octal
    const binToOct = (input: InputNumber) => {
      outputNumber.value = parseInt(input.toString(), 2).toString(8);
    };
    // 3. binary to hex
    const binToHex = (input: InputNumber) => {
      outputNumber.value = parseInt(input.toString(), 2).toString(16);
    };

    // Octal to orthers
    // 1. octal to decimal
    const octToDec = (input: InputNumber) => {
      outputNumber.value = parseInt(input.toString(), 8);
    };
    // 2. octal to binary
    const octToBin = (input: InputNumber) => {
      outputNumber.value = parseInt(input.toString(), 8).toString(2);
    };
    // 3. octal to hex
    const octToHex = (input: InputNumber) => {
      outputNumber.value = parseInt(input.toString(), 8).toString(16);
    };

    // Hex to orthers
    // 1. hex to decimal
    const hexToDec = (input: InputNumber) => {
      outputNumber.value = parseInt(input.toString(), 16);
    };
    // 2. hex to octal
    const hexToOct = (input: InputNumber) => {
      outputNumber.value = parseInt(input.toString(), 16).toString(8);
    };
    // 3. hex to binary
    const hexToBin = (input: InputNumber) => {
      outputNumber.value = parseInt(input.toString(), 16).toString(2);
    };

    const convert = (
      fromFormat: string,
      toFormat: string,
      inputNumber: InputNumber
    ) => {
      if (inputNumber == "") {
        return;
      } else {
        // From decimal
        if (fromFormat == "decimal") {
          if (toFormat == "binary") {
            decToBin(inputNumber);
          } else if (toFormat == "octal") {
            decToOct(inputNumber);
          } else if (toFormat == "hexadecimal") {
            decToHex(inputNumber);
          }
        }
        // From binary
        else if (fromFormat == "binary") {
          if (toFormat == "decimal") {
            binToDec(inputNumber);
          } else if (toFormat == "octal") {
            binToOct(inputNumber);
          } else if (toFormat == "hexadecimal") {
            binToHex(inputNumber);
          }
        }
        // From octal
        else if (fromFormat == "octal") {
          if (toFormat == "decimal") {
            octToDec(inputNumber);
          } else if (toFormat == "binary") {
            octToBin(inputNumber);
          } else if (toFormat == "hexadecimal") {
            octToHex(inputNumber);
          }
        }
        // From hexa
        else if (fromFormat == "hexadecimal") {
          if (toFormat == "decimal") {
            hexToDec(inputNumber);
          } else if (toFormat == "octal") {
            hexToOct(inputNumber);
          } else if (toFormat == "binary") {
            hexToBin(inputNumber);
          }
        }
      }
    };

    return {
      inputNumber,
      outputNumber,
      numberSystems,
      clearInput,
      convert,
      inputFormat,
      outputFormat,
    };
  },
});
</script>
