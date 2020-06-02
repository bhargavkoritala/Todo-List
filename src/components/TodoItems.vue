<template>
    <div v-bind:class="{'complete':message.completed}">  
        <p>
            <input type="checkbox" v-on:change="changeStatus()"/>
            {{message.title}}
            <button @click="$emit('deltodo',message.id)" class="btn">x</button>
        </p>
    </div>
</template>

<script>
export default {
    name:"TodoItems",
    props:["message"],
    methods:{
        changeStatus(){
            console.log(123)
            this.message.completed = !this.message.completed
        }
    }
}
</script>

<style scoped>
.complete{
    text-decoration: line-through;
}
p{
    text-align: center;
}
</style>