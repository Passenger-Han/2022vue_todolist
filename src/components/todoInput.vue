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
</template>

<script>
export default {
    data(){
        return {
            newTodoItem: '',
        }
    },

    methods: {
        todoItem: function(){
            this.$emit('addTodo', this.newTodoItem);
            this.newTodoItem = '';
        }
    },
}
</script>

<style lang="scss">
    .input {
        display: flex;
        margin-bottom: 8px;

        #input {
            flex: 1 0 auto;
            text-indent: 10px;
        }

        .btn {
            line-height: 40px;
            
            padding: 0 10px;
            background: gray;
            color: white;
        }
    }
</style>