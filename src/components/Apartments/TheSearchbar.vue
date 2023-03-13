<template>
    <div class="container py-4">
        <div class="row align-items-center gy-3">
            <div class="col-12 col-sm-8 col-md-5 col-lg-4">
                <div
                    class="input-group searchbar py-2 px-3 rounded-5 align-items-center shadow d-flex justify-content-between">
                    <div class="px-2">
                        <input type="text" class="form-control input-text" placeholder="Cittá"
                            aria-label="Recipient's username" aria-describedby="basic-addon2">
                    </div>

                    <button class="btn my-btn-orange rounded-circle" type="button"><i class="fa fa-search"></i></button>
                </div>
            </div>

            <div class="col">
                <div class="nput-group searchbar py-2 px-3 rounded-5 shadow d-flex">
                    <label for=""><small>Prezzo</small></label>
                    <select class="form-select form-select-sm my-select-control" aria-label=".form-select-sm example">
                        <option disabled selected>-</option>
                        <option value="1">0 - 50€</option>
                        <option value="2">50€ - 100€</option>
                        <option value="3"> > 100€</option>
                    </select>
                </div>
            </div>

            <div class="col">
                <div class="nput-group searchbar py-2 px-3 rounded-5 shadow d-flex">
                    <label for=""><small>Stanze</small></label>
                    <select class="form-select form-select-sm my-select-control" aria-label=".form-select-sm example">
                        <option disabled selected>-</option>
                        <option value="1">One</option>
                        <option value="2">Two</option>
                        <option value="3">Three</option>
                    </select>
                </div>
            </div>

            <div class="col">
                <div class="nput-group searchbar py-2 px-3 rounded-5 shadow d-flex">
                    <label for=""><small>Bagni</small></label>
                    <select class="form-select form-select-sm my-select-control" aria-label=".form-select-sm example">
                        <option disabled selected>-</option>
                        <option value="1">One</option>
                        <option value="2">Two</option>
                        <option value="3">Three</option>
                    </select>
                </div>
            </div>

            <div class="col">
                <div class="nput-group searchbar py-2 px-3 rounded-5 shadow d-flex">
                    <label for=""><small>Letti</small></label>
                    <select class="form-select form-select-sm my-select-control" aria-label=".form-select-sm example">
                        <option disabled selected>-</option>
                        <option value="1">One</option>
                        <option value="2">Two</option>
                        <option value="3">Three</option>
                    </select>
                </div>
            </div>

            <div class="col">
                <div class="nput-group searchbar py-2 px-3 rounded-5 shadow d-flex">
                    <label for=""><small>m²</small></label>
                    <select class="form-select form-select-sm my-select-control" aria-label=".form-select-sm example">
                        <option disabled selected>-</option>
                        <option value="1">One</option>
                        <option value="2">Two</option>
                        <option value="3">Three</option>
                    </select>
                </div>
            </div>
        </div>
    </div>
</template>

<script></script>

<style scoped lang="scss">
@use '../../styles/partials/variables';

.searchbar {
    background-color: white;

    .form-control {
        border: 0;
        padding: 0;

        &:focus {
            border-color: transparent;
            outline: 0;
            box-shadow: 0 0 0 0 white !important;
        }
    }
}

.my-select-control{
    border: none;

    &:focus {
            border-color: transparent;
            outline: 0;
            box-shadow: 0 0 0 0 white !important;
        }
}
</style>