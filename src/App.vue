<script setup>
import { ref } from 'vue';
import BaseModalWindow from './components/Base/Modal/BaseModalWindow.vue';
import OrderDetailsModal from './components/Modals/OrderDetailsModal.vue';
import BaseButtonNonColor from './components/UI-components/Buttons/BaseButtonNonColor.vue';

const isOpenModal = ref(true);

// handle click outside modal and changed visible
function handleClickOutside(event) {
  const modal = event.target.closest('.base-modal__container');
  const target = event.target;

  if (!modal && isOpenModal.value && !target.closest('.button-non-color')) {
    toggleModalVisibility();
  }
}

// toggle visibility modal window
function toggleModalVisibility() {
  isOpenModal.value = !isOpenModal.value;
}
</script>

<template>
  <div class="wrapper" @click="handleClickOutside">
    <BaseButtonNonColor v-if="!isOpenModal" @click="toggleModalVisibility">Открыть форму</BaseButtonNonColor>

    <BaseModalWindow v-if="isOpenModal" title="Отказаться от выполнения заказа" :isOpen="isOpenModal"
      :onClose="toggleModalVisibility">
      <OrderDetailsModal></OrderDetailsModal>
    </BaseModalWindow>
  </div>
</template>

<style lang="scss" scoped>
.wrapper {
  padding: 40px;
  background-color: #e4e4e4;

  .button-non-color {
    width: 220px;
    height: 68px;
    margin: 20px;
  }
}
</style>
