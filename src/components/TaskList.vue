<template>  
    <div>
        <transition-group name="fade" tag="ul"> 
            <ListItem 
                v-for="todo in todos"
                :key="todo._id"
                v-bind:text="todo.text"
                v-bind:completed="todo.completed"
                v-bind:_id="todo._id"
            />
        </transition-group>
    </div>
    
</template>

<script>
import ListItem from './ListItem'

export default {
    name:'TaskList',
    props: ['todos'],
    components: {
        ListItem
    }
}
</script>

<style>
ul {
    padding: 0;
}

.fade-enter-active, .fade-leave-active{
    transition: opacity 1s;
}

.fade-enter, .fade-leave-to {
    opacity: 0;
}
</style>
