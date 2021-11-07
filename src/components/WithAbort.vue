<script setup lang="ts">
import { onMounted, onUnmounted, ref } from "vue";

const controller = new AbortController();
const isLoading = ref(false);
const data = ref<any[]>([]);

onMounted(async () => {
  try {
    isLoading.value = true;
    setTimeout(async () => {
      const rawResult = await fetch(
        "https://jsonplaceholder.typicode.com/todos",
        { signal: controller.signal }
      );
      const result = await rawResult.json();
      data.value = result;
      isLoading.value = false;
    }, 2000);
  } catch (error) {
    console.log(error);
  }
});

onUnmounted(() => {
  controller.abort();
});
</script>

<template>
  <div class="container">
    <h1>WithOutAbort {{ isLoading ? "Loading ...." : null }}</h1>
  </div>
</template>

<style>
.container {
  display: grid;
  place-content: center;
}
</style>
