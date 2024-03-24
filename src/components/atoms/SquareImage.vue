<script setup>
defineProps({
  image: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <span class="square-image">
    <img :src="image.thumbnail" />
  </span>
</template>

<style lang="scss" scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.square-image h1,
.square-image h3 {
  text-align: center;
}

.square-image {
  height: 100%;

  > img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}

@media (min-width: 1024px) {
  .square-image h1,
  .square-image h3 {
    text-align: left;
  }
}
</style>
