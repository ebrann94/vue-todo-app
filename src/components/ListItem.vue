<template>
    <div 
        class="todo" 
        v-bind:class="{completed}"
        @click="completeItem"
    >
        <p>{{text}}</p>
        <input 
            type="checkbox" 
            v-bind:checked="completed"
            @change.prevent="completeItem"
        />
        <button @click="deleteItem">Delete</button>
    </div>
</template>

<script>

export default {
    name: 'ListItem',
    props: ['text', 'completed', '_id'],
    methods: {
        completeItem() {
            this.$parent.$parent.$emit('completeItem', this._id);
        },
        deleteItem() {
            this.$parent.$parent.$emit('deleteItem', this._id);
        }
    }
}
</script>

<style>
.todo {
    border: solid black 1px;
}

.completed {
    background: lightgreen;
}

</style>
