<script>
export default {
    emits: ['delete-done'],
    methods: {
        todoAdd() {
            this.$emit('add-todo', this.newTodoText)
        }
    }
}
</script>

<template>
    <input type="text" v-model="newTodoText" />
    <button @click="todoAdd">追加</button>
    <button @click="this.$emit('delete-done')">完了済みを削除する</button>
  

</template>