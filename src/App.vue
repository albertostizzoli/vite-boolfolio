<template> 
  <router-view></router-view>
</template>

<script>
import { store } from './store.js';

export default {
  name: 'App',
  data() {
    return {
      store,
    }
  },
  
}
</script>

<style lang="scss" scoped>
</style>
