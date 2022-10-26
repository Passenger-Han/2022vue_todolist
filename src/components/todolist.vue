<template>
    <ul class="list">
        <template v-if="todoItem.length == 0">
            <li>
                NO DATA!
            </li>
        </template>
        <template v-for="(item, i) in todoItem" :key="i">
            <li>
                <p class="name">{{ item }}</p>
                <div class="crud-btn">
                    <span @click="Remove(i, item)">지우기</span>
                    <!-- <span>바꾸기</span> -->
                </div>
            </li>
        </template>
    </ul>
</template>

<script>
export default {
    props: [
        'todoItem',
    ],

    methods: {
        Remove(index, item){
            this.$emit('remove', index, item);
        },
    },
}
</script>

<style lang="scss">
    .list {
        margin-bottom: 8px;

        display: flex;
        flex-direction: column;
        gap: 4px;

        li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 8px;

            width: 100%;
            padding: 12px 8px;

            background: lightgray;
            border-radius: 4px;

            .name {
                // width: 80%;
                word-break: break-word;
            }

            .crud-btn {
                // width: 10%;
                flex-basis: 37%;
                flex-shrink: 0;

                display: flex;
                gap: 4px;

                font-size: 0.75em;
                font-style: normal;

                span {
                    flex-basis: 25%;
                    flex-grow: 1;

                    border: 1px solid #000;
                    border-radius: 6px;
                    padding: 4px;
                    text-align: center;
                }
            }
        }
    }
</style>