<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <div style="
      width: 1180px;
      min-height: 748px;
      position: relative;
      margin: 0 auto 0 auto;
    ">
    <header>
      <nav class="navbar navbar-expand-lg navbar-light" style="
          width: 1180px;
          height: 122px;
          -webkit-border-radius: 0 0 30px 30px;
          border-radius: 0 0 30px 30px;
          background-color: #2f4b8f;
          position: relative;
          z-index: 99;
          padding: 15px;
          -webkit-box-sizing: border-box;
          -moz-box-sizing: border-box;
          box-sizing: border-box;
        ">
        <div class="container-fluid">
          <RouterLink to="/" class="navbar-brand">
            <img src="src/assets/logo.png" width="150" height="80" />
          </RouterLink>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
            aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
              <li class="nav-item">
                <RouterLink to="/" class="nav-link text-white letter h4">Home</RouterLink>
              </li>
            </ul>
          </div>
          <div class="position-relative">
            <RouterLink to="/order" class="text-decoration-none">
              <span class="navbar-text border rounded wagen">
                &nbsp;&nbsp;<i style="color: #2f4b8f;" class="bi bi-cart4 h4"></i>&nbsp;&nbsp;
              </span>
              <span
                class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger p-2">{{ items }}</span>
            </RouterLink>
          </div>
        </div>
      </nav>
    </header>
    <br />
    <RouterView />
  </div>
</template>

<style scoped>
.letter {
  font-family: Amain;
}

.wagen {
  border-color: white;
  background-color: white;
}
</style>

<script>
import axios from 'axios'
export default {
  mounted() {
    this.getitems()
  },
  data() {
    return {
      items: 0,
    }
  },
  methods: {
    getitems() {
      axios.get('https://i454010core.venus.fhict.nl/api/Order/itemcount/', {
        params: {
          ID: 1
        }
      })
        .then((response) => {
          this.items = response.data
        })
        .catch((error) => {
          console.log(error)
        })
    }
  }
}
</script>