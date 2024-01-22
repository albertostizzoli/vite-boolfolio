<template> 
<AppHeader />
  <router-view></router-view>
  <AppFooter />
</template>

<script>
import { store } from './store.js';
import AppHeader from "./components/AppHeader.vue";
import AppFooter from "./components/AppFooter.vue";
export default {
  name: 'App',
  components: {
      AppHeader,
      AppFooter
  },
  data() {
    return {
      store,
    }
  },
  
}
</script>

<style lang="scss" scoped>
</style>
