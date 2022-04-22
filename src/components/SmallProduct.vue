<script setup>
import ProductAmount from "@/components/ProductAmount.vue";
defineProps(['name', 'price', 'id', 'stock'])

</script>

<template>
    <div class="col">
        <div class="card">
            <div class="card-header">
                <h5 class="text-center ">{{ name }}</h5>
            </div>
            <div class="card-body">
                <p class="text-end letter">{{ price }}</p>
                <ProductAmount :pid="id" :pstock="stock" />
            </div>
        </div>
    </div>
</template>

<style scoped>
    .letter {
      font-family: Amain;
    }
</style>