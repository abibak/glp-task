<script setup>
import { defineProps, defineEmits, ref } from 'vue';

const emit = defineEmits(['add-reason']);

const props = defineProps({
    label: {
        type: String,
        required: true,
    }
});

const isChecked = ref(false);

// toggle checkbox value and call emit
function toggleCheckbox() {
    isChecked.value = !isChecked.value;
    emit('add-reason', props.label);
}
</script>

<template>
    <div class="custom-checkbox">
        <label class="container">
            <input type="checkbox" id="checkbox" name="checkbox-name" :value="label" :checked="isChecked" @input="toggleCheckbox">
            <span class="checkbox-mark">
                <div class="checked"></div>
            </span>
            <span class="label">{{ label }}</span>
        </label>
    </div>
</template>

<style lang="scss" scoped>
.custom-checkbox {
    .container {
        display: flex;
        width: 100%;
        position: relative;
        margin-bottom: 40px;
    }

    .label {
        padding-left: 73px;
        height: 41px;
        line-height: 41px;
        text-transform: uppercase;
    }

    #checkbox {
        opacity: 0;
        position: absolute;
    }

    #checkbox:checked + .checkbox-mark > .checked {
        opacity: 1;
    }

    .checkbox-mark {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 41px;
        height: 41px;
        border: 4px solid #58595B;
        border-radius: 6px;
        cursor: pointer;
        position: absolute;
        left: 0;
        top: 0;
    }

    .checked {
        @extend .checkbox-mark;
        display: block;
        opacity: 0;
        width: 28px;
        height: 28px;
        border: none;
        left: unset;
        top: unset;
        background-color: #CD10FF;
        transition: opacity .2s ease-in-out;
    }
}

@keyframes checkedAnimation {
        from {
            background-color: transparent;
        }

        to {
            background-color: #CD10FF;
        }
    }
</style>