<template>
    <div>
        <div  v-bind:key="item.id" v-for="item in list">
            <TodoItems v-on:deltodo="$emit('del-todo',item.id)" v-bind:message="item"/>
        </div>
    </div>
</template>

<script>
import TodoItems from './TodoItems.vue'
export default {
    name: 'Todos',
    components: {
     TodoItems
    },
    props:["list"]
}
</script>