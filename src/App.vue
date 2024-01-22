<template> 
<AppHeader />
  <router-view></router-view>
</template>

<script>
import { store } from './store.js';
import AppHeader from "./components/AppHeader.vue";
export default {
  name: 'App',
  components: {
      AppHeader
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
