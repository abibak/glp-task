<script setup>

</script>

<template>
    <div class="button-non-color">
        <button>
            <slot></slot>
        </button>
    </div>
</template>

<style lang="scss" scoped>
button {
    display: inline-block;
    font-family: 'Rubik', sans-serif;
    max-width: inherit;
    width: 100%;
    height: inherit;
    border: 1px solid #CD10FF;
    background-color: #fff;
    border-radius: 12px;
    font-size: 20px;
    font-weight: 500;
    text-transform: uppercase;
    cursor: pointer;
}
</style>