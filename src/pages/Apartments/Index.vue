<template>
    <TheNavbar></TheNavbar>

    <TheSearchbar @searchApartments="saveApartments()"></TheSearchbar>

    <!-- lista appartamenti -->
    <section class="container apartments-list">
        <div class="row">
            <!-- v-for="(apartment, i) in apartments" :key="i" -->
            <!-- Messaggio di mancanza appartamenti  -->
            <div class="mt-3" v-if="apartments.length === 0">
                <div class="alert bg-sabbia text-center" role="alert">
                    Non ci sono risultati per questi filtri
                </div>
            </div>
            <div class="col-12 " v-for="(apartment, i) in apartments" :key="i">
                <!-- Aggiungere :apartment="apartment"-->
                <CardApartment :apartment="apartment"></CardApartment>
            </div>
            <div class="col-12 col-sm-5"></div>
        </div>
    </section>
</template>

<script>
import TheNavbar from '../../components/Apartments/TheNavbar.vue';
import TheSearchbar from "../../components/Apartments/TheSearchbar.vue";
import CardApartment from '../../components/Apartments/CardApartment.vue';
import axios from "axios";
import { store } from "../../store"

export default {
    name: 'ApartmentIndex',
    components: { TheNavbar, TheSearchbar, CardApartment },
    data() {
        return {
            store,
            apartments: []
        }
    },
    methods: {
        fetchIndexApartments() {
            axios.get("http://127.0.0.1:8000/api/apartments/index")
                .then((resp) => {
                    this.apartments = resp.data
                })

        },
        saveApartments() {
            this.apartments = this.store.searchedApartment;

        }
    },
    beforeMount() {
        this.fetchIndexApartments();
    }
}
</script>

<style scoped lang="scss"></style>