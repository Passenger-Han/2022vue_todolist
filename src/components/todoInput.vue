<template>
    <div class="input">
        <input
            type="text"
            name=""
            id="input"
            placeholder="오늘의 할 일을 입력하세요."
            v-model="newTodoItem"
        >
        <div class="btn" @click="todoItem">할 일</div>
    </div>
    <transition name="modalTransition">
    <Modal v-if="viewModal" @closeModal="viewModal = false">
        <template v-slot:ModalHeader>등록 실패</template>
        <template v-slot:ModalBody>할 일을 입력하지 않으셨습니다.</template>
    </Modal>
    </transition>
</template>

<script>
import Modal from './todoModal.vue'

export default {
    components: {
        Modal,
    },

    data(){
        return {
            newTodoItem: '',
            viewModal: false,
        }
    },

    methods: {
        todoItem: function(){
            if (this.newTodoItem != ''){
                let value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.newTodoItem = '';
            } else {
                this.viewModal = true;
            }
        }
    },
}
</script>

<style lang="scss">
    .input {
        display: flex;
        gap: 8px;

        margin-bottom: 8px;

        #input {
            flex: 1 0 auto;
            text-indent: 10px;

            border: 1px solid #00000033;
            border-radius: 4px;
        }

        .btn {
            line-height: 40px;
            
            padding: 0 10px;
            background: gray;
            color: white;
            border-radius: 4px;
        }
    }

    .modalTransition-enter-from {opacity: 0; transform: translate(-50%, -55%);}
    .modalTransition-enter-active {transition: 0.4s;}
    .modalTransition-enter-to {opacity: 1; transform: translate(-50%, -50%);}

    .modalTransition-leave-from {opacity: 1;}
    .modalTransition-leave-active {transition: 0.4s;}
    .modalTransition-leave-to {opacity: 0;}
</style>