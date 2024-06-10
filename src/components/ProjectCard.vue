<script>
export default {
    name: 'ProjectCard',
    props: {
        projectDetails: Object
    },
    methods: {
        truncateText(text) {
            if(text.length > 100) {
                return text.substr(0, 99) + '...';
            }

            return text;
        }
    }
}
</script>

<template>
    <div class="col">
        <div class="card my-3">
            <!-- <img src="..." class="card-img-top" alt="..."> -->
            <div class="card-body">
                <h5 class="card-title">{{ projectDetails.name }}</h5>
                <p class="card-text">{{ truncateText(projectDetails.summary) }}</p>
                 <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->
            </div>
        </div>
    </div>
</template>