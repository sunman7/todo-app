<template>
    <div class="todo-list">
        <ListItem v-for="todo in todos" :key="todo.id" :todo-item="todo"
                  @change="todo.completed = $event.target.checked"></ListItem>
    </div>
</template>

<script type="text/ecmascript-6">
    import ListItem from "./ListItem";

    export default {
        components: {
            ListItem
        },
        props: ["todos"]

    }
    ;
</script>

<style scoped>
    .todo-list {
        display: grid;
        row-gap: 14px;
    }

</style>
