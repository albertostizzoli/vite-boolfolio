<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <h1 v-if="project">{{ project.title }}</h1>
                <div class="d-flex justify-content-between">
                    <div>
                        <p>{{ project.description }}</p>
                        <h4>Repo GitHub:</h4>
                        <button class="btn btn-primary">
                            <a class="text-white text-decoration-none" :href="project.url">Clicca qui</a>
                        </button>
                        <div class="mt-3">
                            <h4>Tipo:</h4>
                            <p class="badge text-bg-primary p-3">{{ project.type.name }}</p>
                        </div>
                        <div class="mb-3">
                            <h4>Tecnologie:</h4>
                            <ul>
                                <li class="badge rounded-pill text-bg-warning p-3"
                                    v-for="technology in project.technologies">{{ technology.name }}</li>
                            </ul>
                        </div>
                        <div>
                            <img class="img" :src="`${store.apiImg}${project.image}`" :alt="project.title">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import { store } from '../store.js';
export default {
    name: 'SingleProject',
    data() {
        return {
            store,
            project: null
        }
    },
    methods: {
        getProjectData() {
            axios.get(this.store.apiUrl + "projects/" + this.$route.params.slug).then((res) => {
                if (res.data.results) {
                    this.project = res.data.results;
                } else {
                    this.$router.push({ name: "not-found" });
                }
            });
        }
    },
    created() {
        this.getProjectData();
    }
}
</script>

<style lang="scss" scoped>
.img {
    height: 300px;
    object-fit: cover;
}

li {
    list-style-type: none;
}
</style>