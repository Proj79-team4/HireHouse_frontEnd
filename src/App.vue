<script>
import TheNavbarHome from './components/TheNavbarHome.vue';
import TheHeaderHome from './components/TheHeaderHome.vue'

export default{
  components:{
    TheNavbarHome,
    TheHeaderHome
  }
}
</script>

<template>
  <TheNavbarHome></TheNavbarHome>
  <TheHeaderHome></TheHeaderHome>

  <router-view></router-view>
</template>

<style lang="scss">
@use "./styles/general.scss";

</style>
