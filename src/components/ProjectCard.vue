<script>
export default {
    name: 'ProjectCard',
    props: {
        projectDetails: {
            type: Object,
            required: true
        }
    },
    methods: {
        truncateText(text) {
            if (text.length > 100) {
                return text.substr(0, 99) + '...';
            }
            return text;
        }
    },
    mounted() {

    }
}
</script>

<template>
    <div class="col">
        <div class="card my-3">
            <!-- <img src="..." class="card-img-top" alt="..."> -->
            <div class="card-body">
                <h5 class="card-title">{{ projectDetails.name }}</h5>
                <div v-if="projectDetails.type">
                    <strong>Tipo</strong>: <span>{{ projectDetails.type.name }}</span>
                </div>
                <p class="card-text">{{ truncateText(projectDetails.summary) }}</p>
                <router-link :to="{ name: 'single-project', params: {slug: projectDetails.slug } }" class="btn btn-primary">Dettagli</router-link>
            </div>
        </div>
    </div>
</template>