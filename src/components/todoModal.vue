<template>
    <div class="modal">
        <h4>
            <slot name="ModalHeader"></slot>
        </h4>
        <p>
            <slot name="ModalBody"></slot>
        </p>
        <button @click="$emit('closeModal')">닫기</button>
    </div>
</template>

<script>
export default {

}
</script>

<style>
button {
    padding: 8px 12px;
}

.modal {
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 8px;

    width: 300px;
    height: 180px;
    background: black;
    color: white;
    border: 1px solid #666;
    border-radius: 16px;
    box-shadow: 4px 4px 8px #33333376;
}
</style>