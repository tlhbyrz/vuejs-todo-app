<template>
    <div :class="[task.reminder ? 'task reminder' : 'task']">
        <section class="task-content">
            <h3>{{ task.text }}</h3>
            <p>{{ task.date }}</p>
        </section>
        <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </div>
</template>

<script>
export default {
    name: "Tasks",
    props: {
        task: Object
    }
}
</script>


<style scoped>
.task{
    display: flex;
    align-items: center;
    width: 100%;
    padding: 15px;
    border-radius: 8px;
    background: #3F87F51A;
    color: #3F87F5;
    margin-bottom: 12px;
    border-left: 10px solid #876cff00;
}
.reminder{
    border-left: 10px solid #886CFF;
}
.task-content{
    flex: 1;
}
.fas{
    font-size: 20px;
    margin-right: 10px;
    color: red;
    cursor: pointer;
}

</style>