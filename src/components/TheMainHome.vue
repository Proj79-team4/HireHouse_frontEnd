<template>
    <section class="bg-white py-5 mt-2">
        <div class="container">

            <!-- consigliati -->
            <h2 class="pb-3">I nostri consigliati</h2>
            <div class="row row-cols-1 row-cols-md-4 gy-3">
                <div class="col" v-for="n in 4">
                    <div class="card p-0 positision-relative" style="">
                        <img src="/Firenze.jpg" class="card-img-top" alt="...">

                        <div class="card-body" :style="{ 'background-color': randomColor() }">
                            <h5 class="card-title">Localitá</h5>
                            <div class="card-subtitle">Nome Appartamento</div>
                            <p class="card-text text-end pt-5">€99,00 notte</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- host -->
            <div class="py-5 host-image position-relative">
                <img src="/pet_casa.jpeg" class="img-fluid w-100 h-100" alt="">

                <div class="position-absolute host-text">
                    <h2>Diventa <br> anche tu <br> un host</h2>
                    <a class="btn my-btn-turchese mt-4">Registrati</a>
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
export default {
    data() {
        return {
            paletteColor: [
                "#0FA3B1",
                "#B5E2FA",
                "#EDDEA4",
                "#F7A072"
            ]
        }
    },
    beforeMount() {

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
</style>