<template>

    <div class="add-section">

        <input v-model="content" placeholder="Task name">
        <button @click="addTask(content)">+</button>

    </div>
    
</template>

<script>
export default {
    name: 'NewToDo',

    data() {
        return {
            content: ''
        }
    },

    methods: {
        addTask(content) {
            if(content != '') {
                this.$emit('newTask', this.content)
                this.content = null
            } else {
                return 0
            }
        }
    }
}
</script>

<style>

    .add-section {
        margin-left: 35%;
        width: 100%;
    }

    .add-section input {
        border: none;
        background-color: rgb(172, 172, 172);
        padding: 10px;
        border-radius: 50px;
        outline: none;
    }

    .add-section button {
        border-radius: 30px;
        width: 50px;
        border: none;
        background-color: rgb(30, 207, 207);
        color: white;
        font-size: 2rem;
        margin-left: 30px;
        cursor: pointer;
        outline: none;
    }

</style>