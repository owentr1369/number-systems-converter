<template>
  <div class="app">
    <app-header></app-header>
    <router-view />
  </div>
</template>

<script lang="ts">
import AppHeader from "@/components/AppHeader.vue";

export default {
  components: {
    AppHeader,
  },
};
</script>

