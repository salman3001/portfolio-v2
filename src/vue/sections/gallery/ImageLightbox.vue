<script setup>
import { useEasyLightbox } from "vue-easy-lightbox";

const props = defineProps({
  images: Array,
  imgMaxHeight: String,
  imgMaxWidth: String,
});

const {
  // methods
  show,
  onHide,
  // changeIndex,
  // refs
  visibleRef,
  indexRef,
  imgsRef,
} = useEasyLightbox({
  // src / src[]
  imgs: props.images,
  // initial index
  initIndex: 0,
});
</script>

<template>
  <div>
    <vue-easy-lightbox
      :visible="visibleRef"
      :imgs="images"
      :index="indexRef"
      @hide="onHide"
    />
    <div class="img-container">
      <img
        v-for="(img, i) in images"
        :key="i"
        class="border"
        :src="img"
        :height="imgMaxHeight || '140'"
        :style="{ maxWidth: imgMaxWidth || ' 150' }"
        @click="
          () => {
            indexRef = i;
            show();
          }
        "
      />
    </div>
  </div>
</template>

<style scoped>
img:hover {
  cursor: pointer;
}

.img-container {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
}
</style>
