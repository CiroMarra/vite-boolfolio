<script>
import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue';

export default {
    name: 'ProjectList',
    components: {
        ProjectCard

    },
    data() {
        return {
            projects: []
        };
    },

    methods: {
        getProjects (pageNumber) {
            axios.get('http://127.0.0.1:8000/api/projects')
            .then((response) => {
                console.log(response);
                this.projects = response.data.results
        
        })

        }
    },
    mounted() {
        this.getProjects();
    }

}

</script>

<template>
    <div class="container">
        <h1>Tutti i progetti</h1>
        <div class="row row-cols-3">
            <ProjectCard v-for="project in projects" :projectDetails="project" :key="project.id"></ProjectCard>
        </div>
    </div>
</template>

<style scoped lang="scss">
</style>