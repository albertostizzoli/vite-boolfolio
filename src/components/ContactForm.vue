<template>
    <form @submit.prevent="submitForm()">
        <div class="mb-3">
            <label for="name" class="form-label">Name</label>
            <input type="text" class="form-control" id="name" aria-describedby="emailHelp" v-model="name">
            <div id="nameHelp" class="form-text">Insert your name.</div>
        </div>
        <div class="mb-3">
            <label for="exampleInputEmail1" class="form-label">Email address</label>
            <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" v-model="email">
            <div id="emailHelp" class="form-text">Insert your mail</div>
        </div>
        <div class="mb-3">
            <label for="address" class="form-label">address</label>
            <input type="text" class="form-control" id="address" aria-describedby="addressHelp" v-model="address">
            <div id="addressHelp" class="form-text">Insert your address.</div>
        </div>
        <div class="mb-3">
            <label for="message" class="form-label">Message</label>
            <textarea name="message" class="form-control" id="message" aria-describedby="addressHelp" v-model="message"></textarea>
            <div id="messageHelp" class="form-text">Insert your message</div>
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
    </form>
</template>

<script>
import axios from 'axios';
import {store} from '../store.js';
export default {
    name: 'ContactForm',
    data(){
        return{
            store,
            name: '',
            email: '',
            address: '',
            message: ''
        }
    },
    methods:{
        submitForm(){
            const data = {
                name: this.name,
                email: this.email,
                address: this.address,
                message: this.message
            };
            axios.post(`${this.store.apiUrl}/contacts`, data).then((res) =>{
                console.log(res.data);
                this.name = '';
                this.email = '';
                this.address = '';
                this.message = '';
            }).catch((err) =>{
                console.log('error', err)
            });
        },
    }
}
</script>

<style lang="scss" scoped></style>