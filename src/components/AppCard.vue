<template>
    <router-link class="col-12 col-md-4 col-lg-3" :to="{ name: 'single-project', params: { slug: project.slug } }">
        <img :src="`${store.apiImg}${project.image}`" class="card-img-top" alt="...">
        <div class="card my-3 d-flex justify-content-center align-items-center">
            <div class="card-body">
                <h3 class="card-title">{{ project.title }}</h3>
            </div>
        </div>
    </router-link>
</template>

<script>
import { store } from '../store.js'
export default {
    name: 'AppCard',
    props: ['project'],
    data() {
        return {
            store,
        }
    }
}
</script>

<style lang="scss" scoped></style>