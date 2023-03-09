<template>
    <section class="bg-white py-5 mt-2">
        <div class="container">
            <h2 class="pb-3">I nostri consigliati</h2>

            <div class="row row-cols-1 row-cols-md-4 gy-3">
                <div class="col" v-for="n in 4">
                    <div class="card p-0 positision-relative" style="">
                        <img src="/Firenze.jpg" class="card-img-top" alt="...">

                        <div class="card-body" :style="{'background-color':randomColor()}">
                            <h5 class="card-title">Localitá</h5>
                            <div class="card-subtitle">Nome Appartamento</div>
                            <p class="card-text text-end pt-5">€99,00 notte</p>
                        </div>
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
    beforeMount(){

    },
    methods: {
        getRandomItem(arr) {
            // get random index value
            const randomIndex = Math.floor(Math.random() * arr.length);

            // get random item
            const item = arr[randomIndex];

            return item;
        },

        randomColor(){
            return this.getRandomItem(this.paletteColor);
        } 
    },
}
</script>

<style scoped lang="scss"></style>