<template>
<div @click="$emit('deleted')">
        <slot></slot>
</div>
</template>

<script>
export default {

}
</script>

<style scoped>
div {
    margin-top: 10px;
    color: #222;
    font-size: 1.5em;
    font-style: italic;
}
div:hover {
    color: red;
}
</style>