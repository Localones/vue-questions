<template>
    <form action="">
        <div class="help">
            <slot name="help"></slot>
        </div>
        <div class="fields">
            <slot name="fields"></slot>
        </div>
        <div class="buttons">
            <slot name="buttons"></slot>
        </div>
    </form>
</template>

<script>
    export default {
        name: "CustomForm"
    }
</script>

<style scoped>

</style>