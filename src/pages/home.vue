<template>
    <TheNavbarHome></TheNavbarHome>
    <TheHeaderHome></TheHeaderHome>
    <TheMainHome></TheMainHome>

</template>

<script>
import TheNavbarHome from '../components/TheNavbarHome.vue';
import TheHeaderHome from '../components/TheHeaderHome.vue';
import TheMainHome from "../components/TheMainHome.vue";

export default {
    name: 'HomePage',
    components: {TheHeaderHome, TheMainHome, TheNavbarHome},
    data() {
        return {
            
        }
    },
}

</script>