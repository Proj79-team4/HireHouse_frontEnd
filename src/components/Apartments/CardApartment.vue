<template>
    <!-- <router-link :to="{name: 'apartments.show', params: {id:apartment.id}}" class="card-title h5 mb-4">
            {{ project.title }}
        </router-link> -->
    <a class="card rounded-4">
        <div class="row no-gutters py-3 border-top">
            <div class="col-12 col-sm-5">
                <img src="/Milano.jpg" class="img-fluid h-100 w-100 rounded-4" alt="">
            </div>
            <div class="col">
                <div class="card-block pt-2">
                    <h6 class="card-subtitle mb-2 text-muted">Indirizzo completo</h6>
                    <h5 class="card-title text-dark">Nome Appartamento</h5>
                    <div class="line"></div>
                    <div class="text-dark"><small>3 Stanze · 3 Letti · 3 Bagni · 145 m²</small></div>
                    <div class="line"></div>
                    <div class="text-dark">86 Visite</div>
                    <div class="text-dark text-end pt-3"><strong>€ 70,00</strong> /notte</div>
                </div>
            </div>
        </div>
    </a>
</template>

<script>
export default{
    // props: {
    //     apartment: {
    //         type:Object,
    //         required: true,
    //         default: ()=>({})
    //     }
    // },
}
</script>

<style scoped lang="scss">
.card {
    border: none;
    text-decoration: none;


    .line {
        border: 1px solid #dee2e6;
        width: 3rem;
        margin: 1rem 0;
    }
}
</style>