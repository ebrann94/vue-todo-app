<template>
    <div>
        <form @submit.prevent="handleSubmit">
            <input type="text" name="text" v-model="textInput" />
            <input type="submit" />
        </form>
    </div>
</template>

<script>
export default {
    name: 'AddItem',
    data: function() {
        return {
            textInput: ''
        }
    },
    methods: {
        handleSubmit: function() {
            this.$emit('addItem', this.textInput);
        }
    }
}
</script>

<style>

</style>
