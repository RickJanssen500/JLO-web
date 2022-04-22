

<script setup>
import CartItem from "@/components/CartItem.vue";
</script>

<template>
    
        <!-- fix var link met eigen api als gehost -->
        <CartItem v-for="Product in Products" :key="Product.id" :name="Product.product.name" :price="Product.product.price" :id="Product.id" :amount="Product.amount" />

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
                axios.get('https://i454010core.venus.fhict.nl/api/Order/getcart/1')
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