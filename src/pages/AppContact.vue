<template>
    <div>
        <h1>Contattami</h1>
        <ContactForm />
    </div>
</template>

<script>
import ContactForm from '../components/ContactForm.vue';
export default {
    components:{ ContactForm },
    name: 'AppContact',
    data(){
        return{

        }
    }
}
</script>

<style lang="scss" scoped></style>