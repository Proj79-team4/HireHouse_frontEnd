<template>
    <div class="container py-4">
        <div class="row align-items-center gy-3">
            <div class="col-6 col-md-3">
                <div class="input-group searchbar py-2 px-3 rounded-5 align-items-center shadow d-flex justify-content-between">
                    <div class="px-2">
                        <input type="text" class="form-control input-text" placeholder="Cittá"
                            aria-label="Recipient's username" aria-describedby="basic-addon2" v-model="address" >
                    </div>
                    <!-- <button class="btn my-btn-orange rounded-circle" type="button"><i class="fa fa-search"></i></button> -->
                </div>
            </div>

            <div class="col-6 col-md-3">
                <div class="input-group searchbar py-2 px-3 rounded-5 shadow d-flex align-items-center">
                    <label for=""><small>Prezzo</small></label>
                    <select class="form-select form-select-sm my-select-control" aria-label=".form-select-sm example"
                        v-model="form.price">
                        <option disabled selected>-</option>
                        <option value="50"> &lt 50€</option>
                        <option value="100"> &lt 100€</option>
                        <option value="150"> 150€ </option>
                    </select>
                </div>
            </div>

            <div class="col-6 col-md-3">
                <div class="input-group searchbar py-2 px-3 rounded-5 shadow d-flex align-items-center">
                    <label for="roomInput"><small>Stanze: </small></label>
                    <input type="number" class="form-control form-control-sm my-select-control ps-1" id="roomInput" placeholder=""
                        v-model="form.num_rooms">
                </div>
            </div>

            <div class="col-6 col-md-3">
                <div class="input-group searchbar py-2 px-3 rounded-5 shadow d-flex align-items-center">
                    <label for="bathInput"><small>Bagni: </small></label>
                    <input type="number" class="form-control form-control-sm my-select-control ps-1" id="bathInput" placeholder=""
                        v-model="form.num_bathrooms">

                </div>
            </div>

            <div class="col-6 col-md-3">
                <div class="input-group searchbar py-2 px-3 rounded-5 shadow d-flex align-items-center">
                    <label for="bedInput"><small>Letti: </small></label>
                    <input type="number" class="form-control form-control-sm my-select-control ps-1" id="bedInput" placeholder=""
                        v-model="form.num_beds">

                </div>
            </div>

            <div class="col-6 col-md-3">
                <div class="input-group searchbar py-2 px-3 rounded-5 shadow d-flex align-items-center">
                    <label for="meterInput"><small>m²: </small></label>
                    <input type="number" class="form-control form-control-sm my-select-control ps-1" id="meterhInput" placeholder=""
                        v-model="form.square_meters">
                </div>
            </div>

            <div class="col-6 col-md-3">
                <div class="input-group searchbar py-2 px-3 rounded-5 shadow d-flex flex-column justify-content-center">
                    <label for="distanceInput" class="flex-fill"><small>Distanza: <output id="value">{{ form.dist }} km</output></small></label>
                    <input id="distanceInput" type="range" min="0" max="500" step="5" class="form-range w-100" v-model="form.dist"/>
                </div>
            </div>

            <div class="col-6 col-md-3 d-flex justify-content-center">
                <button class="btn my-btn-orange rounded-pill w-50 shadow" @click="fetchApartments()">Cerca</button>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import {store} from "../../store"
export default {
    data() {
        return {
            store,
            address: store.city,
            form: {
                price: "",
                num_rooms: "",
                num_bathrooms: "",
                num_beds: "",
                square_meters: "",
                lat: "",
                lng: "",
                dist: 20,
            }

        }
    },
    mounted(){
        if(this.address != ""){
            this.fetchApartments();
        }
    },
    methods: {
        fetchApartments() {
            axios.get("https://api.tomtom.com/search/2/geocode/" + this.address + ".json?key=6hakT8QU7IRSx9PCHGi5JyHTV2S7xWlD")
                .then((resp) => {
                    this.form.lat = resp.data.results[0].position.lat
                    this.form.lng = resp.data.results[0].position.lon


                    //chiamata axios per recuperare gli appartmaenti con i fltri
                    axios.get("http://127.0.0.1:8000/api/apartments/research", { params: this.form })
                        .then((resp) => {
                            
                            store.searchedApartment=resp.data
                            this.$emit("searchApartments");

                        }
                    )

                }

            )
        }
    }

}


</script>

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

.my-select-control {
    border: none;

    &:focus {
        border-color: transparent;
        outline: 0;
        box-shadow: 0 0 0 0 white !important;
    }
}

input[type="range"]::-webkit-slider-thumb {
   background-color: #F7A072;
}
</style>