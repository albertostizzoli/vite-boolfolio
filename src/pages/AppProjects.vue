<template>
    <main class="container">
        <h1>Progetti</h1>
        <div class="row">
            <div class="col-12 col-md-4 col-lg-3" v-for="project in projects" :key="project.id">
                <AppCard :project="project" />
            </div>
        </div>
    </main>
    <button class="btn btn-danger me-2" @click="previousPage()">Indietro</button>
    <button class="btn btn-success ms-2" @click="nextPage()">Avanti</button>
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
            axios.get(store.apiUrl + "projects", { params: { page: this.currentPage } }).then((res) => {
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