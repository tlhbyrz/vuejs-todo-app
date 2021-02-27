<template>
    <header>
        <h1>{{ title }}</h1>
        <Button text="Add task" @click="onClick"/>
    </header>
</template>

<script>
import Button from "./Button"

export default{
    name: "Header",
    props: {
        title: String
    },
    components:{
        Button
    },
    methods: {
        onClick() {
            alert("test")
        }
    }    
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