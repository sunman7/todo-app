<template>
    <main>
        <div class="container">
            <h1>记录你接下来要做的事吧~</h1>
            <Add :tid="todos.length" @add-todo="addTodo"></Add>
            <Filter :selected="filter" @change-filter="filter = $event"></Filter>
            <List :todos="filteredTodos"></List>
        </div>
    </main>
</template>

<script>

    import List from "./components/List";
    import Add from "./components/Add";
    import Filter from "./components/Filter";
    import {computed, ref} from "vue";

    export default {
        name: "App",
        components: {
            List, Add, Filter
        },
        setup() {
            const filter = ref("all");
            const filteredTodos = computed(() => {
                switch (filter.value) {
                    case "done":
                        return todos.value.filter((todo) => todo.completed);
                    case "todo":
                        return todos.value.filter((todo) => !todo.completed);
                    default:
                        return todos.value;
                }
            });
            const todos = ref([]);
            const addTodo = (todo) => todos.value.push(todo);
            return {
                todos, addTodo, filter, filteredTodos
            };
        }
    };
</script>

<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
        font-family: Helvetica, "PingFang SC", "Microsoft YaHei UI", sans-serif;
    }

    main {
        width: 100vw;
        min-height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        background: rgb(203, 210, 240);
    }

    .container {
        width: 80%;
        max-width: 400px;
        box-shadow: 0px 0px 24px rgba(0, 0, 0, 0.15);
        border-radius: 24px;
        padding: 48px 28px;
        background: rgba(245, 246, 252);
    }

    h1 {
        margin: 24px 0;
        font-size: 28px;
        color: #414873;
        text-align: center;
    }


</style>
