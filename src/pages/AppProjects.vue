<template>
    <div>
        <ul>
            <li v-for="project in projects" :key="project.slug">
                <router-link :to="{name: 'single-project', params: {slug: project.slug}}" class="btn btn-primary">{{ project.title }}</router-link>
            </li>
        </ul>
        <button @click="previousPage()">Indietro</button>
        <button @click="nextPage()">Avanti</button>
    </div>
</template>

<script>
import axios from "axios";
import { store } from '../store.js';
import AppCard from '../components/AppCard.vue';
export default {
    name: 'AppProjects',
    components: {
       AppCard
    },
    data() {
        return {
            store,
            projects: [],
            currentPage: 1,
            lastPage: 0,
        }
    },
    methods: {
        getAllProjects() {
            axios.get(store.apiUrl + "/projects", { params: { page: this.currentPage } }).then((res) => {
                console.log(res.data);
                this.projects = res.data.results.data;
                console.log(this.projects);
                this.currentPage = res.data.results.current_page;
                this.lastPage = res.data.results.last_page;
            });
        },
        nextPage() {
            if (this.currentPage < this.lastPage) {
                this.currentPage += 1;
                this.getAllProjects();
            }
        },
        previousPage() {
            if (this.currentPage > 0) {
                this.currentPage -= 1;
                this.getAllProjects();
            }
        }
    },
    mounted() {
        this.getAllProjects();
    }
}


</script>

<style lang="scss" scoped></style>