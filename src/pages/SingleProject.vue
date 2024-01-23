<template>
    <div>
        <h1 v-if="project">{{ project.title }}</h1>
        <img :src="`${store.apiImg}${project.image}`" :alt="project.title">
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

<style lang="scss" scoped></style>