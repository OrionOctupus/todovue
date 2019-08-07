<template>
    <div>
        <ul>
            <TodoItems/>
        </ul>
    </div>
</template>

<script>
import TodoItems from '@/components/TodoItems';
export default {
    props: ['namevar'],
    components : {
        TodoItems
    }
}
</script>
