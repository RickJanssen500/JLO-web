<script setup>
import SmallProduct from "@/components/SmallProduct.vue";
</script>

<template>
    <div class="row row-cols-1 row-cols-md-4 g-4">
        <!-- fix var link met eigen api als gehost -->
        <SmallProduct v-for="Product in Products" :key="Product.id" :name="Product.name" :price="Product.price" :id="Product.id" :stock="Product.stock" />
    </div>
</template>

<script>
import axios from 'axios'
    export default {
        mounted() {
            this.getproducts()
        },
        data() {
            return {
                Products: [],
            }
        },
        methods: {
            getproducts() {
                axios.get('https://i454010core.venus.fhict.nl/api/product/get')
                .then((response) => {
                    this.Products = response.data
                })
                .catch((error) =>{
                    console.log(error)
                })
            }
        }
}
</script>