<template>
    <TheNavbar></TheNavbar>

    <main class="container">
        <!-- jumbotron -->
        <section class="py-4" v-if="apartment != null">
            <h2>{{ apartment.title }}</h2>
            <div> <span class="text-muted">{{ apartment.full_address }}</span></div>

            <div class="apartment-image">
                <img :src="'http://127.0.0.1:8000/' + 'storage/' + apartment.cover_img" class="rounded-4">
            </div>
        </section>

        <div class="row "  v-if="apartment != null">
            <!-- informazioni appartamento -->
            <div class="col-12 col-lg-8 pe-5">
                <section>
                    <div class="row border-bottom pb-3">
                        <div class="col-9">
                            <h4>Host: {{ apartment.user.name +" "+ apartment.user.surname }}</h4>
                            <div class="fw-bold"><small>{{ apartment.num_rooms }} Stanze · {{ apartment.num_beds }} Letti · {{
                                apartment.num_bathrooms }} Bagni · {{ apartment.square_meters }} m²</small></div>
                        </div>
                        <div class="col-3 d-flex justify-content-end">
                            <div class="host-img">
                                <img :src="'http://127.0.0.1:8000/' + 'storage/' + apartment.user.profile_image" class="img-fluid" alt="">
                            </div>
                        </div>
                    </div>


                    <p class="lead py-4 border-bottom m-0" v-if="apartment.description">
                        {{ apartment.description }}
                    </p>

                    <div class="row pb-3 border-bottom">
                        <div class="col-12 col-sm-6">
                            <!-- servizi -->
                            <div class="py-3">
                                <h5 class="py-3">Servizi appartamento</h5>
                                <div v-for="(service,i) in apartment.services" class="py-1 px-4">
                                    <i :class="'fa-solid ' + service.icon  "></i>
                                    <span class="ps-3">{{ service.name }}</span>
                                </div>
                            </div>
                        </div>
                        <div class="col-12 col-sm-6">
                            <!-- Regole -->
                            <div class="py-3">
                                <h5 class="py-3">Regole appartamento</h5>
                                <div v-for="(rule,i) in apartment.rules" class="py-1 px-4">
                                    <i :class="'fa-solid ' + rule.icon  "></i>
                                    <span class="ps-3">{{ rule.name }}</span>
                                </div>
                            </div>
                        </div>
                    </div>

                </section>

                <!-- mappa -->
                <section>
                    <div class="py-3">
                        <h4 class="py-3">Posizione</h4>
                    </div>
                </section>
            </div>

            <!-- form messaggi -->
            <div class="col-12 col-lg-4 py-4">
                <div class="shadow p-3 rounded-4">
                    <h5 class="text-center py-3">€{{ apartment.price }} /notte</h5>
                    <form action="" method="">
                        <div class="pt-2 px-3 border rounded-top">
                            <label for="exampleFormControlInput1" class="fw-bold"><small>NOME</small></label>
                            <input type="text" class="form-control form-control-sm" id="exampleFormControlInput1" placeholder="Inserisci il tuo nome">
                        </div>
                        <div class="pt-2 px-3 border border-top-0">
                            <label for="exampleFormControlInput1" class="fw-bold"><small>E-MAIL</small></label>
                            <input type="email" class="form-control form-control-sm" id="exampleFormControlInput1" placeholder="Inserisci la tua email">
                        </div>
                        <div class="pt-2 px-3 border border-top-0 rounded-bottom mb-2">
                            <label for="exampleFormControlTextarea1" class="fw-bold"><small>INSERISCI MESSAGGIO</small></label>
                            <textarea class="form-control form-control-sm" id="exampleFormControlTextarea1" rows="3" placeholder="Scrivi qui"></textarea>
                        </div>

                        <a href="" class="btn my-btn-orange d-block">Invia</a>
                    </form>
                </div>
            </div>
        </div>
    </main>

    <TheFooter></TheFooter>
</template>

<script>
import TheNavbar from '../../components/Apartments/TheNavbar.vue';
import TheFooter from '../../components/TheFooter.vue';
import axios from "axios"; 

export default {
    name: 'ApartmentShow',
    components: { TheNavbar, TheFooter },
    data() {
        return {
            apartment: null
        }
    },
    methods:{
        fetchIndexApartments(){
            axios.get("http://127.0.0.1:8000/api/apartments/show/"+this.$route.params.id)
            .then((resp)=>{
                this.apartment=resp.data
            })

        }
    },
    beforeMount(){
        this.fetchIndexApartments();
    }

}
</script>

<style scoped lang="scss">
@use '../../styles/partials/variables';
.apartment-image {
    height: 60vh;
    padding: 2rem 0;

    img {
        object-fit: cover;
        width: 100%;
        height: 100%;
        display: block;
    }
}

.host-img {
    max-width: 5rem;
    border-radius: 50%;
    aspect-ratio: 1/1;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;

    img {
        object-fit: cover;
    }
}

form {
    .form-control{
        border: 0;
        padding: 0;
        margin: 0;

        &:focus {
            color: #212529;
            background-color: #fff;
            border-color: #F7A072;
            outline: 0;
            box-shadow: 0 0 0 0;
        }
    }
}

</style>