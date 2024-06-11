<script>
import axios from 'axios';

export default {
    name: 'SingleProject',
    data() {
        return {
            projects: null
        };
    },
    methods: {
        getProjectDetails() {
            axios.get(`http://127.0.0.1:8000/api/projects/${this.$route.params.slug}`)
            .then((response) => {
                this.projects = response.data.result;
                console.log(response.data.result);
            });
        }
    },
    mounted() {
        this.getProjectDetails(); 
    }
}
</script>

<template>
    <div class="container">
        <div v-if="projects"> 
            <h1>{{ projects.name }}</h1> 

            <div v-if="projects.cover_image">
                <img :src="`http://127.0.0.1:8000/storage/${projects.cover_image}`" :alt="projects.name"> 
            </div>

            <p v-if="projects.summary">
                {{ projects.summary }}
            </p>
        </div>
    </div>
</template>