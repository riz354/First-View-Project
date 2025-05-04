<script >

export default {
    data (){
        return {
            name : "Rizwan Asghar",
            status: "active",
            tasks :['task1','task2'],
            link : "https://www.google.co.uk/"
        }
    },
    methods:{
        toggleStatus(){
            if(this.status === "active"){
                this.status = "pending"
            }else if (this.status === "pending"){
                 this.status = "inactive"
            }else {
                 this.status = "inactive"
            }
        }
    }
}
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status">Status is {{ status }}</p>
  <p >Tasks : </p>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <!-- <a v-bind:href="link">Click here to gogle</a> -->
  <a :href="link">Click here to gogle</a>

  <button v-on:click="toggleStatus">Change Status</button>


</template>

