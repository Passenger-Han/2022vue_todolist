<template>
    <div class="removeAll" @click="$emit('removeAll')">
        모두 지우기
    </div>
</template>

<script>
export default {

}
</script>

<style>
    .removeAll {
        display: flex;
        justify-content: center;
        align-items: center;

        padding: 12px 0;

        background: darkgray;
        color: white;
        border-radius: 4px;
    }
</style>