<script setup>
defineProps(['name', 'price', 'prodid', 'amount'])
</script>

<template>
    <div class="card">
        <div class="card-body">
            <div class="d-flex justify-content-between">
                <p class="letter">{{ name }} - {{ price }} </p>
                <p class="letter">aantal {{ amount }}</p>
                <button type="button" v-on:click="delitem()" class="btn btn-danger letter">X</button>
            </div>
        </div>
    </div>
    <br>
</template>

<style scoped>
.letter {
    font-family: Amain;
}
</style>

<script>
import axios from 'axios'
export default {

    methods: {
        delitem() {
            axios.delete('https://i454010core.venus.fhict.nl/api/Order/Del/1/'+this.prodid)
            .then(response => {window.location.reload()})
            .catch(function (error) {
                console.log(error);
            })            
        }
    }
}
</script>