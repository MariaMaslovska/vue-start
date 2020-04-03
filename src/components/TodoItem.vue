<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox"
            @change="todo.completed=!todo.completed">
            <strong>{{ index + 1 }}</strong>
            {{ todo.title | uppercase}} 
        </span>
        <button class="rm" @click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
       todo:{
            type: Object,
            required: true
       },
       index: Number
    },
    filters:{
        uppercase(value){
            return value.toUpperCase()
        }
    }
}
</script>

<style scoped>
li{
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
}
.rm{
    height: 23px;
    width: 23px;
    background: red;
    color: white;
    font-weight: bold;
}
.done{
    text-decoration: line-through;
}
input{
    margin-right: 1rem;
    height:18px;
    width: 18px;
}
</style>