<template>
    <div class="nocomp">
        <h3>Not complete</h3>
        <app-todo v-for="(element, index) in todos" v-if="element.done !== true">
            <span @click="element.done = !element.done" :class="{ icon__complete: element.done }">
                <span class="icon__check"><i :class="[element.done?'far fa-check-square':'far fa-square']"></i></span>
                    {{element.name}}
            </span>
            <span class="icon__delete"><i class="far fa-trash-alt" @click.prevent="deleteTodo(index)"></i></span>
        </app-todo>
    </div>
</template>

<script>
    import Todo from './Todo.vue';

    export default {
        props: ['todos'],
        components: {
            appTodo: Todo
        },
        methods: {
            deleteTodo(index) {
                this.$emit('todoDeleted', index);
            }
        }
    }
</script>

<style>

</style>