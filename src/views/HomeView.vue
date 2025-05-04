<script setup>
import Hero from "@/components/Hero.vue";
import Homecard from "@/components/Homecard.vue";
import JobListings from "@/components/JobListings.vue";
</script>

<template>
    <Hero title="Test" subTitle="Test Subtitle" />
    <Homecard />
    <JobListings limit=10 showButton=true />
</template>