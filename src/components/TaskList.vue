<template>  
    <div>
        <transition-group name="fade" tag="ul"> 
            <ListItem 
                v-for="todo in todos"
                v-bind:key="todo._id"
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

.fade-enter {
    opacity: 0;
    max-height: 0px;
}

.fade-enter-to {
    max-height: 100px;
    opacity: 1;
    transition: all 200ms;
}

.fade-leave {
    max-height: 50px;
    opacity: 1;
    overflow: hidden;
} 

.fade-leave-to {
    max-height: 0px;
    opacity: 0;
    transition: all 200ms;
    overflow: hidden;
}

</style>
