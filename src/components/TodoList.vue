<template>
    <div>
        <ul>
            <TodoItems v-for="(toll, i) of namevar" v-bind:toll="toll" v-bind:index="i" v-on:remove-todo="removeTodo"/>
        </ul>
    </div>
</template>

<script>
import TodoItems from '@/components/TodoItems';
export default {
    props: ['namevar'],
    components : {
        TodoItems
    },
    methods: {
        removeTodo(id) {
            console.log(id)
            this.$emit('remove-todo', id)
        }
    }
}
</script>

<style scoped>  
ul {
    list-style: none;
    margin: 0;
    padding: 0;
}

</style>
