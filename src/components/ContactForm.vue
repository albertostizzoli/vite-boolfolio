<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <form @submit.prevent="submitForm">
                    <div class="mb-3">
                        <label for="name" class="form-label">Name</label>
                        <input type="text" class="form-control" id="name" aria-describedby="emailHelp"
                            v-model="newMail.name">
                        <div id="nameHelp" class="form-text">Insert your name.</div>
                    </div>
                    <div class="mb-3">
                        <label for="exampleInputEmail1" class="form-label">Email address</label>
                        <input type="email" class="form-control" id="email" aria-describedby="emailHelp"
                            v-model="newMail.email">
                        <div id="emailHelp" class="form-text">Insert your mail</div>
                    </div>
                    <div class="mb-3">
                        <label for="address" class="form-label">address</label>
                        <input type="text" class="form-control" id="address" aria-describedby="addressHelp"
                            v-model="newMail.address">
                        <div id="addressHelp" class="form-text">Insert your address.</div>
                    </div>
                    <div class="mb-3">
                        <label for="message" class="form-label">Message</label>
                        <textarea name="message" class="form-control" id="message" aria-describedby="addressHelp"
                            v-model="newMail.message"></textarea>
                        <div id="messageHelp" class="form-text">Insert your message</div>
                    </div>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import { store } from '../store.js';
export default {
    name: 'ContactForm',
    data() {
        return {
            store,
            newMail: {
                name: '',
                email: '',
                address: '',
                message: ''
            },
        }
    },
    methods: {
        submitForm() {
            axios.post(this.store.apiUrl + 'contacts', this.newMail).then((res) => {
                console.log(res);
                this.newMail = {
                    name: '',
                    email: '',
                    address: '',
                    message: '',
                }
            })
        },
    }
}
</script>

<style lang="scss" scoped></style>