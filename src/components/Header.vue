<template>
    <div>
        <h1>Todo List</h1>
        <h2>{{text}}</h2>
    </div>
</template>

<script>
export default {
    name: 'Header',
    props: {
        text: String
    }
}
</script>

<style>

</style>
