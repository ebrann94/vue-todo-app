<template>
    <div class="add-item">
        <form @submit.prevent="handleSubmit" class="add-item__form">
            <input
                    type="text"
                    name="text"
                    v-model="textInput"
                    class="add-item__text"
                    placeholder="Add Item"
            />
            <input type="submit" value="+" class="add-item__submit"/>
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
            if (this.textInput) {
                this.$emit('addItem', this.textInput);
                this.textInput = '';
            }
        }
    }
}
</script>

<style>
 .add-item__form {
     height: 32px;
     font-size: 1em;
 }

.add-item__text {
    width: 256px;
    height: 32px;
    padding: 8px;
    border-radius: 4px 0 0 4px;
    /*border: solid rgb(200, 200, 200);*/
    /*border-width: 0 1px 1px 0;*/
    border: none;
    outline: none;
    margin: 0;

    font-family: inherit;
    font-size: inherit;
}

.add-item__submit {
    -webkit-appearance: none;
    -moz-appearance: none;

    height: 100%;
    width: 48px;
    border: none;
    border-radius: 0 4px 4px 0;
    background: rgba(205, 205, 205, 0.94);

    padding: 0;
    cursor: pointer;

    font-family: inherit;
    font-size: inherit;
    font-weight: 700;
    line-height: 1;
}

 .add-item__submit:hover {
     background: rgba(160, 160, 160, 0.94);
 }

</style>
