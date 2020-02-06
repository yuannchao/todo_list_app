<template>
    <div class="container">
        <app-header v-model="todos" :todoCount="completeTodo" :maxTodos="todos.length"></app-header>
        <app-form @todoAdded="newTodo"></app-form>
        <app-perfect-scrollbar>
            <app-nocomp-grid :todos="todos" @todoDeleted="deleteTodo"></app-nocomp-grid>
        </app-perfect-scrollbar>
        <app-perfect-scrollbar>
        <app-comp-grid :todos="todos" @todoDeleted="deleteTodo"></app-comp-grid>
        </app-perfect-scrollbar>
    </div>
</template>

<script>
    import NocompGrid from './components/NocompGrid.vue';
    import CompGrid from './components/CompGrid.vue';
    import Form from './components/Form.vue';
    import Header from './components/Header.vue';
    import { PerfectScrollbar } from 'vue2-perfect-scrollbar';

    export default {
        data: function () {
            return {
                todos: [
                    { name: 'Buy some pet food', done: false },
                    { name: 'Clean room', done: false },
                    { name: 'Play game', done: true },
                    { name: 'Coding', done: true },
                    { name: 'Read a book', done: false }
                ],
                maxTodos: 20,
            }
        },
        methods: {
            newTodo(todo) {
                if (this.todos.length >= this.maxTodos) {
                    return alert('Please delete Todos first!');
                }
                this.todos.push({
                    name: todo.name,
                    done: false
                    });
            },
            deleteTodo(index) {
                this.todos.splice(index, 1);
            },
        },
        computed: {
            completeTodo() {
                return this.todos.filter(element => element.done === true).length;
            }
        },
        components: {
            appNocompGrid: NocompGrid,
            appForm: Form,
            appHeader: Header,
            appCompGrid: CompGrid,
            appPerfectScrollbar: PerfectScrollbar
        }
    }
</script>

<style lang="sass" src="./assets/sass/main.scss"></style>

<style src="vue2-perfect-scrollbar/dist/vue2-perfect-scrollbar.css">
</style>