<template>
    <TheNavbar></TheNavbar>

    <TheSearchbar></TheSearchbar>

    <!-- lista appartamenti -->
    <section class="container apartments-list">
        <div class="row">
            <!-- v-for="(apartment, i) in apartments" :key="i" -->
            <div class="col-12 col-sm-7" v-for="n in 10">
                <!-- Aggiungere :apartment="apartment"-->
                <CardApartment></CardApartment>
            </div>
            <div class="col-12 col-sm-5"></div>
        </div>
    </section>
</template>

<script>
import TheNavbar from '../../components/Apartments/TheNavbar.vue';
import TheSearchbar from "../../components/Apartments/TheSearchbar.vue";
import CardApartment from '../../components/Apartments/CardApartment.vue';

export default {
    name: 'ApartmentIndex',
    components: { TheNavbar, TheSearchbar, CardApartment },
    data() {
        return {
            //apartments: []
        }
    },
}
</script>

<style scoped lang="scss">
</style>