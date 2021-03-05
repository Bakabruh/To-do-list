<template>
    <div class="card">

        <div class="title">
            <p>{{ date }}</p>
            <h2>{{ titleCard }}</h2>
            <p>{{ tasks.length }} tâches</p>
        </div>

        <section class="main">
            <NewToDo @newTask="sendTask"></NewToDo>

            <ToDoList v-bind:tasks="tasks" v-on:removeTask="deleteTask"></ToDoList>
        </section>

    </div>
</template>

<script>
import NewToDo from './NewToDo'
import ToDoList from './ToDoList'

export default {
    name: "Todocard",

    data() {
        return {
            day: ["Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi", "Dimanche"],
            month: ["Janvier", "Février", "Mars", "Avril", "Mai", "Juin", "Juillet", "Août", "Septembre", "Octobre", "Novembre", "Décembre"],
            titleCard: "VueJs Tutorial ToDo List",
            tasks: []
        }

    },
    computed: {
        date: function() {
            let today = new Date()
            let todate = `${this.day[(today.getDate())-1]}` + ' ' + today.getDate() + ' ' + `${this.month[(today.getMonth())]}` + ' ' + today.getFullYear()
            return todate
        }
    },

    methods: {
        sendTask(payload) {
            this.tasks.push({ name: payload, state: 0 })
            console.log(payload)
        },

        deleteTask(task) {
            this.tasks.splice(task, 1)
        }
    },

    components: {
        NewToDo,
        ToDoList
    }
}
</script>

<style>

    .card {
        display: flex;
        flex-direction: column;
        width: 800px;
        min-height: 300px;
        margin: auto;
    }

    .card .title {
        display: flex;
        justify-content: center;
    }

    .card .title p {
        color: rgb(87, 87, 87);
    }

    .card .title h2 {
        color: rgb(30, 207, 207);
        padding: 0 60px;
    }

</style>