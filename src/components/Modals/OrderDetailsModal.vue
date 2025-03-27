<script setup>
import { ref } from 'vue';
import CustomCheckbox from '../UI-components/Checkboxes/CustomCheckbox.vue';

// list values for checkboxes
const listReasons = ref([
    'Не подходит дата или время',
    'Не подходит тоннаж груза',
    'Не подходит объем груза',
    'Не подходит тип фургона',
    'Нет пропуска в мкад ттк ск',
    'Поломка машины/авария',
    'Заболел',
    'Нет санобработки',
    'Нет мед. книжки',
    'Нет Гидроборта',
    'Нет растентовки',
    'Не устраивает ставка за рейс',
    'Не устраивает маршрут',
    'Другое',
]);

const selectedValues = ref([]);

// adding reason value in list or delete if contain
function addReason(value) {
    const foundResult = selectedValues.value.indexOf(value);

    if (foundResult > -1) {
        selectedValues.value.splice(foundResult, 1);
    } else {
        selectedValues.value.push(value);
    }
}
</script>

<template>
    <div class="order-details-modal">
        <div class="order-details-modal__checkbox-item" v-for="reason of listReasons">
            <CustomCheckbox @add-reason="addReason" :label="reason"></CustomCheckbox>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.order-details-modal {
    max-height: 755px;
    display: inline-block;
    margin: 55px auto 0 auto;
    overflow-y: scroll;
    scrollbar-width: thin;
}
</style>