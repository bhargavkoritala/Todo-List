<template>
    <div>
        <form v-on:submit="add">
            <input type="text" v-model="title" name="title" placeholder="Add a task todo">
            <p>{{title}}</p>
            <button class="btn" type="submit">Submit</button>
        </form>
    </div>
</template>

<script>
export default {
    name:"AddTask",
    data(){
        return{
            title:''
        }
    },
    methods:{
        add(e){
            e.preventDefault()
            const newTask = {
                title:this.title,
                completed:false
            }
            this.$emit("addTask",newTask)
            this.title=''
        }
    }
}
</script>