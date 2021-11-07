<script setup lang="ts">
import WithOutAbort from "./components/WithOutAbort.vue";
import WithAbort from "./components/WithAbort.vue";
import { ref } from "vue";

const toggle = ref(false);

const handleClick = () => {
  toggle.value = !toggle.value;
};
</script>

<template>
  <div>
    <button @click="handleClick">click</button>
    <hr />
    <!-- <WithOutAbort v-if="toggle" /> -->
    <WithAbort v-if="toggle" />
  </div>
</template>

<style></style>
