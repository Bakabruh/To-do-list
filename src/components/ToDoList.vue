<template>
    
    <div class="list" :key="task" v-for="task in tasks">
        <input @click="checker(tasks.indexOf(task))" :id="tasks.indexOf(task)" type="checkbox">
        <label :for="tasks.indexOf(task)" :id="'index' + tasks.indexOf(task)">{{ task.name }}</label>
        <button @click="removeTask(tasks.indexOf(task))"><i class="fas fa-trash"></i></button>
    </div>

</template>

<script>
export default {
    name: "ToDoList",
    props: {
        tasks: {
            type: Array,
            default: () => []
        },
        name: {
            type: String
        }

    },

    methods: {
        checker(task) {
            let checkbox =  document.getElementById(task)

            if(checkbox.checked) {
                document.getElementById('index' + task).className = "disabled"
            } else {
                document.getElementById('index' + task).className = "enabled"
            }
        },

        removeTask(task) {
            this.$emit('removeTask', task)
        }

    },

}
</script>

<style>

    .list {
        display: flex;
        justify-content: space-between;
    }

    .list label {
        margin: 20px 10px;
    }

    .list button {
        border: none;
        width: 40px;
        height: 40px;
        cursor: pointer;
        margin-top: 10px;
    }

    .list input {
        margin-top: 30px;
        border-radius: 20px;
    }

    .list .disabled {
        text-decoration: line-through;
    }

    .list .enabled {
        text-decoration: none;
    }
</style>