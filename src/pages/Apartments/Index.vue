<template>
    <section class="py-3">
        <div class="container d-flex justify-content-between align-items-center">
            <div>
                <a href=""><img src="/Logo-bianco.png" width="200"></a>
            </div>

            <div class="pt-2">
                <a href="" class="nav-link">
                    Torna alla Home
                    <i class="fa-solid fa-house ms-3"></i>
                </a>
            </div>
        </div>
    </section>

    <TheSearchbar></TheSearchbar>

    <!-- lista appartamenti -->
    <section class="container">
        <div class="row">
            <div class="col-8">
                <CardApartment></CardApartment>
            </div>
            <div class="col-4"></div>
        </div>
    </section>
</template>

<script>
import TheSearchbar from "../../components/Apartments/TheSearchbar.vue";
import CardApartment from '../../components/Apartments/CardApartment.vue';

export default {
    name: 'ApartmentIndex',
    components: { TheSearchbar, CardApartment }
}
</script>