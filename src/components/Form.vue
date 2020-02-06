<template>
    <div class="form">
        <input class="form__input" type="text" placeholder="New Todo" v-model="todo.name" v-on:keyup.enter="createItem">
        <button class="form__btn" @click.prevent="createItem">Add !</button>
    </div>
</template>

<script>
    export default {
        data: function() {
            return {
                todo: { name: '', done: false }
            };
        },
        methods: {
            createItem() {
                if(this.todo.name == ""){
                    alert('Please add Todo first!');
                }else{
                    this.$emit('todoAdded', this.todo);
                    this.todo.name = '';
                }
            }
        }
    }
</script>

<style>

</style>