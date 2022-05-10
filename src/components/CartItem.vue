<script setup>
defineProps(['name', 'price', 'id', 'amount'])
</script>

<template>
    <div class="card">
        <div class="card-body">
            <div class="d-flex justify-content-between">
                <p class="letter">{{ name }} - {{ price }} </p>
                <p class="letter">aantal {{ amount }}</p>
                <button type="button" class="btn btn-danger letter">X</button>
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