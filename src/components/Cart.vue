

<script setup>
import CartItem from "@/components/CartItem.vue";
</script>

<template>

   
    <CartItem v-for="Product in Products" :key="Product.id" :name="Product.product.name" :price="Product.product.price"
        :prodid="Product.product.id" :amount="Product.amount" />

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
            axios.get('https://i454010core.venus.fhict.nl/api/Order/getcart/', {
                params: {
                    ID: 1
                }
            })
                .then((response) => {
                    this.Products = response.data
                })
                .catch((error) => {
                    console.log(error)
                })
        }
    }
}
</script>