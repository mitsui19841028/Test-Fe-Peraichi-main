<script setup>
import { ref } from 'vue';
import IconTrashCan from '@/components/icons/IconTrashCan.vue'

const isExpand = ref(false);

const emit = defineEmits([
  'left',
  'right',
  'delete'
]);

defineProps({
  index: {
    type: Number,
    required: true
  }
})

const handleSettingClick = () => {
  isExpand.value = true;
}

const handleEditClick = (operation, index) => {
  isExpand.value = false;

  if (operation === 'left') {
    emit('left', index)
  } else if (operation === 'right') {
    emit('right', index)
  } else if (operation === 'delete') {
    emit('delete', index)
  } else {
    console.log('なんかおかしいよ')
  }
}
</script>

<template>
  <button v-show="!isExpand" class="edit-button" @click="handleSettingClick">Setting</button>
  <span v-show="isExpand" class="edit-button expand">
    <ul>
      <li>
        <button @click="handleEditClick('left', index)" :disabled="index === 0" class="sub-button">
          <span class="icon">←</span>Move left</button
        >
      </li>
      <li>
        <button @click="handleEditClick('right', index)" class="sub-button">
          <span class="icon">→</span>Move right</button
        >
      </li>
      <li>
        <button @click="handleEditClick('delete', index)" class="sub-button delete">
          <span class="icon"><icon-trash-can /></span>Delete</button
        >
      </li>
    </ul>
  </span>
</template>

<style lang="scss" scoped>
.edit-button {
  opacity: 0.5;
  border: none;
  color: white;
  background-color: #999;
  border-radius: 3px;
  padding: 10px;
  /* copy from parent */
  position: absolute;
  top: 10px;
  right: 10px;

  &.expand {
    color: #333;
    opacity: unset;
    background-color: #fff;

    ul {
      list-style: none;
      padding: 0;
      margin: 0;

      li:not(:last-child) {
        border-bottom: 1px solid #000;
      }
    }
  }
}

.sub-button {
  border: none;
  outline: none;
  background: transparent;

  &.delete {
    color: #F00;
  }
}

.icon {
  margin-right: 5px;
}
</style>
