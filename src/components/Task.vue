<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder? 'reminder': '', 'task']">
        <h3>
            {{ task.text }}
            <i @click = "$emit('delete-task', task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{ task.day }}</p>
    </div>
    
</template>

<script>
export default{
    name: 'Task',
    props: {
        task: Object
    }
}
</script>

<style scope>
.task{
    padding: 1px 10px;
    margin-bottom: 20px;
    background-color: rgb(233, 231, 231);
    cursor: pointer;
}

.task h3{
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.fas{
    color: red;
    cursor: pointer
}

.reminder{
    border-left: solid 5px green;
}
</style>