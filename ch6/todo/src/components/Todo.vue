<template>
    <button class="list-group-item text-left" @click="clickButton">{{ label }}</button>
</template>
<script>
export default {
    props: ['label'],
    name: 'todo',
    methods: {
        clickButton() {
            this.$emit('componentClick')
        }
    }
}
</script>

<style>
</style>