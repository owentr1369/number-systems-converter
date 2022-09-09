<template>
  <div class="home">
    <input type="text" placeholder="Enter your number" v-model="inputNumber" />
    <select name="" id=""></select>
    <div class="buttons">
      <button class="convert">Convert</button>
      <button class="clear" v-on:click="clearInput('')">Clear</button>
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

    return { inputNumber, numberSystems, outputNumber, clearInput };
  },
});
</script>
