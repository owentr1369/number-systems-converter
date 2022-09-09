<template>
  <div class="app">
    <app-header></app-header>
    <router-view />
  </div>
</template>

<script lang="ts">
import AppHeader from "@/components/AppHeader.vue";
import { ref } from "@vue/reactivity";

// types
import NumberSystem from "./types/NumberSystem";

export default {
  components: {
    AppHeader,
  },
  setup() {
    const numberSystems = ref<NumberSystem[]>([
      { title: "Binary", value: "binary", id: "1" },
      { title: "Decimal", value: "decimal", id: "2" },
      { title: "Octal", value: "octal", id: "3" },
      { title: "Hexadecimal", value: "hexadecimal", id: "4" },
    ]);

    return { numberSystems };
  },
};
</script>

