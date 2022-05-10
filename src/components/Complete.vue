

<template>
    <h1>hier staan alle producten uit je winkelwagen  
    <button class="btn btn-primary letter" type="button" data-bs-toggle="modal" data-bs-target="#CompleteItem">
        Bestellen
    </button></h1>
    <div class="modal fade" id="CompleteItem" tabindex="-1" aria-labelledby="CompleteItem" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title letter" id="CompleteItemLabel">Bestellen</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
          <p class="letter">ophaal moment</p>
		<input type="datetime-local"  id="Completedate" name="Completedate">
      </div>
      <div class="modal-footer">
        <button type="button" id="completebutton" @click="complete()" class="btn btn-success letter">Bestelling plaatsen</button>
      </div>
    </div>
  </div>
</div>
</template>

<style scoped>
.letter {
    font-family: Amain;
}

.cblack {
    font-family: Amain;
    color: black;
    pointer-events: none;
}
</style>

<script>
import axios from 'axios'
export default {
    methods: {
        complete() {
            axios.post('https://i454010core.venus.fhict.nl/api/Order/CompleteOrder', {
                "Uid": 1,
                "date": document.getElementById('Completedate').value
            })
                .then(response => { window.location.reload() })
                .catch(function (error) {
                    console.log(error);
                })
        }
    }
}
</script>
