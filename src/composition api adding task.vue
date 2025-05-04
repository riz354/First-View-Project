<script setup>

import { ref,onMounted } from "vue";

const name = ref("Rizwan Asghar");
const status = ref("active");
const tasks = ref(['task1', 'task2']);
const link = ref("https://www.google.co.uk/");
const newTask = ref('');


const toggleStatus = () => {
    if (status.value === "active") {
        status.value = "pending"
    } else if (status.value === "pending") {
        status.value = "inactive"
    } else {
        status.value = "inactive"
    }
}

const addTask = () => {
    if (newTask.value.trim() !== '') {
        tasks.value.push(newTask.value);
        newTask.value = '';
    }
}

const deleteTask = (index) => {
        tasks.value.splice(index,1);
}

onMounted  (async () =>{
    try {
        const response = await fetch('https://jsonplaceholder.typicode.com/todos');
        const data = await response.json();
        tasks.value = data.map((task)=>task.title);
    } catch (error) {
        console.log('error fetching tasks');
        
    }
}) 
</script>

<template>
    <form @submit.prevent="addTask">
        <input type="text" id="newTask" name="newTask" v-model="newTask">
        <button type="submit">submit</button>

    </form>
    <h1>{{ name }}</h1>
    <p v-if="status">Status is {{ status }}</p>
    <p>Tasks : </p>
    <ul>
        <li v-for="(task ,index) in tasks" :key="task"> <span>{{ task }}</span> <button @click="deleteTask(index)">x</button></li>
    </ul>
    <!-- <a v-bind:href="link">Click here to gogle</a> -->
    <a :href="link">Click here to gogle</a>

    <button v-on:click="toggleStatus">Change Status</button>


</template>
