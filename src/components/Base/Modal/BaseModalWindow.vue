<script setup>
import { defineProps } from 'vue';
import BaseButtonNonColor from '../../UI-components/Buttons/BaseButtonNonColor.vue';

const props = defineProps({
    title: {
        type: String,
        required: true,
    },
    content: {
        type: [String, Object],
    },
    isOpen: {
        type: Boolean,
        required: true,
    },
    onClose: {
        type: Function,
        required: true,
    }
});

// base method closing modal
function closeModal() {
    props.onClose();
}
</script>

<template>
    <div class="base-modal">
        <div class="base-modal__close" @click="closeModal">
            <svg width="46" height="47" viewBox="0 0 46 47" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    d="M31.4573 18.4852C32.2244 17.7703 32.2667 16.5688 31.5517 15.8017C30.8367 15.0346 29.6353 14.9924 28.8682 15.7073L23.3123 20.8855L18.1341 15.3297C17.4192 14.5626 16.2177 14.5203 15.4506 15.2352C14.6835 15.9502 14.6413 17.1517 15.3562 17.9188L20.5344 23.4746L14.9786 28.6528C14.2115 29.3678 14.1692 30.5692 14.8841 31.3363C15.5991 32.1034 16.8006 32.1457 17.5677 31.4307L23.1235 26.2525L28.3017 31.8084C29.0167 32.5755 30.2181 32.6178 30.9852 31.9028C31.7523 31.1878 31.7946 29.9864 31.0796 29.2193L25.9014 23.6634L31.4573 18.4852Z"
                    fill="#58595B" />
                <path fill-rule="evenodd" clip-rule="evenodd"
                    d="M2.33228 23.5691C2.33228 12.0342 11.6831 2.68337 23.218 2.68337C34.7529 2.68337 44.1038 12.0342 44.1038 23.5691C44.1038 35.104 34.7529 44.4549 23.218 44.4549C11.6831 44.4549 2.33228 35.104 2.33228 23.5691ZM23.218 40.6575C13.7804 40.6575 6.12968 33.0068 6.12968 23.5691C6.12968 14.1315 13.7804 6.48078 23.218 6.48078C32.6557 6.48078 40.3064 14.1315 40.3064 23.5691C40.3064 33.0068 32.6557 40.6575 23.218 40.6575Z"
                    fill="#58595B" />
            </svg>

        </div>

        <div class="base-modal__container">
            <p class="base-modal__title">{{ props.title }}</p>
            <p class="base-modal__order-number">№ У00017711</p>
            <p class="base-modal__reason">Расскажите, почему отказались от выполнения заказа?</p>

            <slot></slot>

            <div class="base-modal__action">
                <BaseButtonNonColor>Отправить</BaseButtonNonColor>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.base-modal {
    max-width: 614px;
    width: 100%;
    margin: 0 auto;
    background-color: #fff;
    border-radius: 45px 45px 0 0;
    border: 1px solid red;
    font-size: 26px;
    position: relative;

    p {
        text-transform: uppercase;
    }

    &__close {
        position: absolute;
        right: 33px;
        top: 22px;
        cursor: pointer;
    }

    &__container {
        text-align: center;
        padding-top: 89px;
        margin-bottom: 145px;
    }

    &__order-number {
        font-weight: bold;
        margin-top: 5px;
    }

    &__reason {
        font-weight: 900;
        margin-top: 40px;
    }

    &__action {
        display: flex;
        justify-content: center;
        align-items: center;
        max-width: 614px;
        width: 100%;
        height: 145px;
        background-color: #fff;
        position: absolute;
        bottom: 0;
        left: 0;

        .button-non-color {
            flex-grow: 1;
            max-width: 512px;
            height: 68px;
        }
    }
}
</style>