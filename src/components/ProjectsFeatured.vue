<script>
import { store } from '../store.js'
import { projects } from '../projects.js'
import ProjectCardFeatured from './ProjectCardFeatured.vue';

export default {
    name: 'ProjectsFeatured',
    components: {
        ProjectCardFeatured
    },
    data() {
        return {
            base_projects_url: '/api/featured',
            projects: projects,
            store,
            isImageBlur: false
        }
    }
}
</script>

<template>
    <div class="container projects_container">
        <div class="projects">
            <ProjectCardFeatured v-for="project in projects" :key="project.id" class="project_card"
                :imageSrc="project.src" />
        </div>
    </div>
</template>

<style scoped>
.projects_container {
    margin-bottom: 5rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    .projects {
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
    }
}

.loader {
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--pf-gray-800);
}

@media screen and (min-width: 720px) {
    .project_card {
        width: calc(100% / 2 - 1rem + (1rem / 3));
    }
}

@media screen and (min-width: 1280px) {
    .project_card {
        width: calc(100% / 3 - 1rem + (1rem / 3));
    }
}
</style>
