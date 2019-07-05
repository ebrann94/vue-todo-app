<template>
    <div class="todo-wrapper">
        <div 
            class="todo" 
            v-bind:class="{completed}"
            @click="completeItem"
        >
            <p class="todo__text">{{text}}</p>
            <div>
                <button @click="deleteItem" class="todo__delete">X</button>
            </div>
        </div>
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
.todo-wrapper {
    width: 100%;
    height: 100%;
}

.todo {
    width: 60%;
    margin: 5px auto;
    padding: 0 0 0 16px;

    background: white;
    /*border: solid rgba(0, 0, 0, 0.1) 1px;*/
    border: none;
    border-radius: 4px;
    box-shadow: 2px 2px 10px rgba(0,0,0,0.2);

    display: flex;
    justify-content: space-between;
    align-items: stretch;
}

.todo__text {
    margin: 10px 0;
}

.todo__delete {
    height: 100%;
    width: 48px;
    -webkit-appearance: none;
    -moz-appearance: none;
    cursor: pointer;

    background: rgb(255,79,79);
    background: linear-gradient(176deg, rgba(255,79,79,1) 0%, rgba(208,0,0,1) 100%);
    color: white;
    border: none;
    border-radius: 0 4px 4px 0;

}

.completed {
    background: rgb(165,241,0);
    background: radial-gradient(circle, rgba(165,241,0,1) 0%, rgba(130,212,0,1) 100%);
    text-decoration: line-through;
}

</style>
