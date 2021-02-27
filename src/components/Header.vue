<template>
    <header>
        <h1>{{ title }}</h1>
        <Button @show-form="$emit('show-form')" :text="showAddForm ? 'Close' : 'Add Task'" :color="showAddForm ? '#DE4436' : '#00C9A7'"/>
    </header>
</template>

<script>
import Button from "./Button"

export default{
    name: "Header",
    props: {
        title: String,
        showAddForm: Boolean
    },
    components:{
        Button
    },
    emits: ["show-form"]    
}
</script>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
    margin-top: 50px;
}
</style>