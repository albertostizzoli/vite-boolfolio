<template>
     <div class="container">
        <div class="row">
            <div class="col-12  mt-5">
                <h1 class="text-center">Vite Boolfolio</h1>
                <p class="text-center">Questa è la HomePage</p>
            </div>
        </div>
    </div>
</template>

<script>
import { store } from '../store.js';
export default {
    name: 'AppHome',
    data(){
        return{
            store,
        }
    },
    methods: {

    }, 

}
</script>

<style lang="scss" scoped></style>