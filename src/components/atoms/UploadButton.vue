<script setup>
const emit = defineEmits(['click'])

defineProps({
  text: {
    type: String,
    required: false
  },
  isDisable: {
    type: Boolean,
    required: false,
    default: false
  }
})

const handleClick = () => {
  emit('click')
}
</script>

<template>
  <button
    class="upload-button"
    @click="handleClick"
    :disabled="isDisable"
  >{{ text }}</button>
</template>

<style lang="scss" scoped>
.upload-button {
  width: 100%;
  border: none;
  color: white;
  background-color: #03D5AC; /* spoited */
  border-radius: 3px;
  padding: 10px;

  &:disabled {
    opacity: 0.5;
    background-color: #333;
  }
}
</style>
