<template>
    <nav class="navbar navbar-expand-lg bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand text-white" href="#">Porfolio</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
      
        <li class="nav-item" v-for="item in menu" :key="index">
            <router-link class="nav-link active text-white" active-class="active" :to="{name: item.name}">{{ item.label }}</router-link>
         
        </li>
       
      </ul>
    </div>
  </div>
</nav>
</template>

<script>
export default {
    name: "AppHeader",
    data(){
        return {
            menu: [
                {
                    label: "Home",
                    name: 'home'
                    
                },
                {
                    label: "Progetti",
                    name: 'projects',
                   
                },
                {
                    label: "Contatti",
                    name: 'contacts',
                   
                },
            ]
        }
    }
}
</script>

<style lang="scss" scoped></style>