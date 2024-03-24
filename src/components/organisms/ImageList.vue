<script setup>
import ImageItem from '@/components/molecules/Image.vue'

defineProps({
  images: {
    type: [Object],
    required: true
  }
})
</script>

<template>
  <span>
    <ul class="fuga">
      <li v-for="(image, index) in images" :key="image.id">
        <image-item
          :image="image"
          :index="index"
          @left="$emit('left', index)"
          @right="$emit('right', index)"
          @delete="$emit('delete', index)"
        />
      </li>
    </ul>
  </span>
</template>

<style lang="scss" scoped>
@import '../../assets/_variables.scss';

.fuga {
  width: 100%;
  list-style: none;
  display: flex;
  justify-content: flex-start;
  padding: 0;

  li:not(:last-child) {
    margin-right: $margin-each-images;
  }
}
</style>
