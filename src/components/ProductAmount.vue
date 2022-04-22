<script setup>
defineProps(['pid', 'pstock'])

</script>

<template>
   <div class="btn-group w-100 mb-1">
  <button @click="min" class="btn btn-secondary letter ">-</button>
  <button class="btn btn-outline-secondary cblack ">{{Amount}}</button>
  <button @click="plus" class="btn btn-secondary letter ">+</button>
</div>
<button class="btn btn-primary letter w-100">toevoegen aan winkelwagen</button>
</template>

<style scoped>
    .letter {
      font-family: Amain;
    }
    .cblack 
    {
        font-family: Amain;
        color: black;
        pointer-events: none;
    }
</style>

<script>
    export default {
        data() {
            return {
                Amount: 0,
            }
        },
        methods: {
            plus() {
                this.Amount++;
                if(this.Amount > this.pstock)
                {
                   this.Amount = this.pstock;
                }
            },
            min() {
                this.Amount-- ;
                if(this.Amount <= -1)
                {
                    this.Amount = 0;
                }
            }
        }
}
</script>