<template>
    <section class="bg-white py-5 mt-2">
        <div class="container">

            <!-- consigliati -->
            <h2 class="pb-3">I nostri consigliati</h2>
            <div class="row row-cols-1 row-cols-md-4 gy-3">
                <div class="col" v-for="apartment in this.apartmentsSponsorized">
                    <router-link :to="{name: 'apartments.show', params: {id:apartment.id}}" class="text-decoration-none text-dark">
                        <div class="card p-0 positision-relative h-100" style="">

                            <!-- Inserire come primo parametro il proprio URL del BackEnd ! -->
                            <img :src="'http://127.0.0.1:8000/' + 'storage/' + apartment.cover_img " class="card-img-top h-50" alt="...">
                            <div class="position-absolute top-0 pt-2 ps-1 translate-middle" v-if="apartment.sponsors.length > 0">
                                <i class="fa-solid fa-star p-1 star"></i>
                            </div>

                            <div class="card-body" :style="{ 'background-color': randomColor() }">
                                <h5 class="card-title">{{apartment.title}}</h5>
                                <div class="card-subtitle">{{apartment.full_address}}</div>
                                <p class="card-text text-end pt-5">€{{apartment.price}} /notte</p>
                            </div>
                        </div>
                    </router-link >
                </div>
            </div>

            <!-- host -->
            <div class="py-5 host-image position-relative">
                <img src="/pet_casa.jpeg" class="img-fluid w-100 h-100" alt="">

                <div class="position-absolute host-text">
                    <h2>Diventa <br> anche tu <br> un host</h2>
                    <a href="http://127.0.0.1:8000/" class="btn my-btn-turchese mt-4">Registrati</a>
                </div>
            </div>

            <!-- principali destinazioni -->
            <div class="container">

                <h3 class="pb-4">Principali destinazioni</h3>

                <div class="row">
                    <div class="col-lg-3 col-md-6">
                        <ul class="list-unstyled mb-0 destinazione">
                            <li class="mb-3">
                                <h6>Roma</h6>
                                <a href="#!" style="color: #4f4f4f;">Lazio</a>
                            </li>
                            <li class="mb-3">
                                <h6>Milano</h6>
                                <a href="#!" style="color: #4f4f4f;">Lombardia</a>
                            </li>
                            <li class="mb-3">
                                <h6>Firenze</h6>
                                <a href="#!" style="color: #4f4f4f;">Toscana</a>
                            </li>
                            <li>
                                <h6>Venezia</h6>
                                <a href="#!" style="color: #4f4f4f;">Veneto</a>
                            </li>
                        </ul>
                    </div>
                    <div class="col-lg-3 col-md-6 mb-4">
                        <ul class="list-unstyled mb-0 destinazione">
                            <li class="mb-3">
                                <h6>Roma</h6>
                                <a href="#!" style="color: #4f4f4f;">Lazio</a>
                            </li>
                            <li class="mb-3">
                                <h6>Milano</h6>
                                <a href="#!" style="color: #4f4f4f;">Lombardia</a>
                            </li>
                            <li class="mb-3">
                                <h6>Firenze</h6>
                                <a href="#!" style="color: #4f4f4f;">Toscana</a>
                            </li>
                            <li>
                                <h6>Venezia</h6>
                                <a href="#!" style="color: #4f4f4f;">Veneto</a>
                            </li>
                        </ul>
                    </div>
                    <div class="col-lg-3 col-md-6 mb-4">
                        <ul class="list-unstyled mb-0 destinazione">
                            <li class="mb-3">
                                <h6>Roma</h6>
                                <a href="#!" style="color: #4f4f4f;">Lazio</a>
                            </li>
                            <li class="mb-3">
                                <h6>Milano</h6>
                                <a href="#!" style="color: #4f4f4f;">Lombardia</a>
                            </li>
                            <li class="mb-3">
                                <h6>Firenze</h6>
                                <a href="#!" style="color: #4f4f4f;">Toscana</a>
                            </li>
                            <li>
                                <h6>Venezia</h6>
                                <a href="#!" style="color: #4f4f4f;">Veneto</a>
                            </li>
                        </ul>
                    </div>
                    <div class="col-lg-3 col-md-6">
                        <ul class="list-unstyled mb-0 destinazione">
                            <li class="mb-3">
                                <h6>Roma</h6>
                                <a href="#!" style="color: #4f4f4f;">Lazio</a>
                            </li>
                            <li class="mb-3">
                                <h6>Milano</h6>
                                <a href="#!" style="color: #4f4f4f;">Lombardia</a>
                            </li>
                            <li class="mb-3">
                                <h6>Firenze</h6>
                                <a href="#!" style="color: #4f4f4f;">Toscana</a>
                            </li>
                            <li>
                                <h6>Venezia</h6>
                                <a href="#!" style="color: #4f4f4f;">Veneto</a>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import axios from "axios"; 

export default {
    data() {
        return {
            paletteColor: [
                "#0FA3B1",
                "#B5E2FA",
                "#EDDEA4",
                "#F7A072"
            ],
            apartmentsSponsorized:[]
        }
    },
    beforeMount() {
        this.fetchSponsorized()
    },
    methods: {
        getRandomItem(arr) {
            // get random index value
            const randomIndex = Math.floor(Math.random() * arr.length);

            // get random item
            const item = arr[randomIndex];

            return item;
        },

        randomColor() {
            return this.getRandomItem(this.paletteColor);
        },

        // Funzione che recupera la lista di appartamenti sponsorizzati
        fetchSponsorized(){
            axios.get("http://127.0.0.1:8000/api/apartments/sponsorized")
                .then((respone)=>{
                    this.apartmentsSponsorized = respone.data;
                })
        }
    },
}
</script>

<style scoped lang="scss">
.host-image {
    height: 700px;

    img {
        object-fit: cover;
        object-position: center;
    }

    .host-text {
        top: 10%;
        right: 10%;

        h2 {
            font-size: 60px;
        }
    }
}

.destinazione {
    li a{
        text-decoration: none;
        padding-bottom: 1rem;
    }

    li h6{
        padding: 0;
        margin: 0;
    }

}
.star{
    color:#ee722f;
    font-size: 25px;
    
}
</style>