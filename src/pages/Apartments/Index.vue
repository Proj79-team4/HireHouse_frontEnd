<template>
    <TheNavbar></TheNavbar>

    <TheSearchbar></TheSearchbar>

    <!-- lista appartamenti -->
    <section class="container apartments-list">
        <div class="row">
            <!-- v-for="(apartment, i) in apartments" :key="i" -->
            <div class="col-12 col-sm-7" v-for="(apartment,i) in apartments" :key="i">
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

export default {
    name: 'ApartmentIndex',
    components: { TheNavbar, TheSearchbar, CardApartment },
    data() {
        return {
            apartments: []
        }
    },
    methods:{
        fetchIndexApartments(){
            axios.get("http://127.0.0.1:8000/api/apartments/index")
            .then((resp)=>{
                this.apartments=resp.data
            })

        }
    },
    beforeMount(){
        this.fetchIndexApartments();
    }
}
</script>

<style scoped lang="scss">
</style>