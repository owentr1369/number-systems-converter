<template>
  <div class="home">
    <input type="text" placeholder="Enter your number" v-model="inputNumber" />
    <select name="" id=""></select>
    <div class="buttons">
      <button class="convert">Convert</button>
      <button class="clear">Clear</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "HomeView",

  setup() {
    const inputNumber = ref("");

    return { inputNumber };
  },
});
</script>
