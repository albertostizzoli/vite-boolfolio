<template>
    <div>
        <h1 class="text-center mt-1 mb-3">Contattami</h1>
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