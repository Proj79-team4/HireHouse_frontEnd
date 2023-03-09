<template>
    <section class="bg-black py-3">
        <div class="container">
            <!-- searchbar -->
            <div class="row">
                <div class="col-12 d-flex justify-content-center">
                    <div class="input-group mb-3 searchbar px-3 py-2 rounded-5 align-items-center">
                        <div class="d-flex flex-column flex-fill px-2">
                            <h6 class="mb-0"><small>Localitá</small></h6>
                            <input type="text" class="form-control input-text" placeholder="Inserisci la tua prossima meta" aria-label="Recipient's username" aria-describedby="basic-addon2">
                        </div>

                        <div class="input-group-append ps-2">
                            <button class="btn my-btn-orange rounded-circle" type="button"><i class="fa fa-search"></i></button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script></script>

<style scoped lang="scss">
@use '../styles/partiarls/variables';
.searchbar {
    width: 70%;
    background-color: white;

    .form-control{
        border: 0;
        padding: 0;

        &:focus {
            border-color: transparent; 
            outline: 0;
            box-shadow: 0 0 0 0 white !important;
        }
    }
}
</style>