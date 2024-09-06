<script setup>
import { computed, onMounted, onUnmounted, ref } from "vue";

const props = defineProps({
  url: String,
});
</script>

<template>
  <iframe height="300" width="100%" :src="url" allowfullscreen> </iframe>
</template>
