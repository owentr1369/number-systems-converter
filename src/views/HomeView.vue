<template>
  <div class="home">
    <input type="text" placeholder="Enter your number" v-model="inputNumber" />
    <select name="" id=""></select>
    <div class="buttons">
      <button class="convert" @click="convert('hello', 'hi')">Convert</button>
      <button class="clear" @click="clearInput('')">Clear</button>
    </div>
    <div class="output">
      <h1>{{ outputNumber }}</h1>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

// types
import NumberSystem from "../types/NumberSystem";

export default defineComponent({
  name: "HomeView",

  setup() {
    const inputNumber = ref<string | number>("");
    const outputNumber = ref<string | number>("");

    const numberSystems = ref<NumberSystem[]>([
      { title: "Binary", value: "binary", id: "1" },
      { title: "Decimal", value: "decimal", id: "2" },
      { title: "Octal", value: "octal", id: "3" },
      { title: "Hexadecimal", value: "hexadecimal", id: "4" },
    ]);

    const clearInput = (input: string) => {
      inputNumber.value = input;
    };

    // Decimal to orthers
    // 1. decimal to binary
    const decToBin = (input: number | string) => {
      alert("decToBin " + input.toString(2));
    };
    // 2. decimal to octal
    const decToOct = (input: number | string) => {
      alert("decToOct " + input.toString(8));
    };
    // 3. decimal to hex
    const decToHex = (input: number | string) => {
      alert("decToHex " + input.toString(16));
    };
    // Binary to orthers
    // 1. binary to decimal
    const binToDec = (input: number | string) => {
      alert("binToDec " + parseInt(input.toString(), 2));
    };
    // 2. binary to octal
    const binToOct = (input: number | string) => {
      alert("binToOct " + parseInt(input.toString(), 2).toString(8));
    };
    // 3. binary to hex
    const binToHex = (input: number | string) => {
      alert(
        "binToHex " + parseInt(input.toString(), 2).toString(16).toUpperCase()
      );
    };
    // Octal to orthers
    // 1. octal to decimal
    const octToDec = (input: number | string) => {
      alert("octToDec " + parseInt(input.toString(), 8));
    };
    // 2. octal to binary
    const octToBin = (input: number | string) => {
      alert("octToBin " + parseInt(input.toString(), 8).toString(2));
    };
    // 3. octal to hex
    const octToHex = (input: number | string) => {
      alert("octToHex " + parseInt(input.toString(), 8).toString(16));
    };
    // Hex to orthers
    // 1. hex to decimal
    const hexToDec = (input: number | string) => {
      alert("hexToDec " + parseInt(input.toString(), 16));
    };
    // 2. hex to octal
    const hexToOct = (input: number | string) => {
      alert("hexToOct " + parseInt(input.toString(), 16).toString(8));
    };
    // 3. hex to binary
    const hexToBin = (input: number | string) => {
      alert("hexToBin " + parseInt(input.toString(), 16).toString(2));
    };

    const convert = (fromFormat: string, toFormat: string) => {
      console.log(fromFormat, toFormat);
    };

    return {
      inputNumber,
      numberSystems,
      outputNumber,
      clearInput,
      convert,
    };
  },
});
</script>
