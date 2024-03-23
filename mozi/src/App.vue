<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue';

const films = ref([])

onMounted(() => {
  axios.get('http://localhost:3000/films')
  .then(resp => films.value = resp.data)
})

const votessw = ref(0)
const incrisesw = () =>
{
  votessw.value++
}


const votesm = ref(0)
const incrisem = () =>
{
  votesm.value++
  
}

const votess = ref(0)
const incrises = () =>
{
  votess.value++
}
</script>

<template>
  <div class="d-flex justify-content-center fw-bold my-2 fs-2 ">
      <p>Filmszemle</p>
  </div>
 <div class="container" >
  <div class="row">
    <div class="row row-cols-1 row-cols-md-3 g-4">
      <div class="col" v-for="f in films">
        <div class="card">
          <img :src="'src/assets/logo.svg'" class="card-img-top w-50" alt="...">
          <div class="card-body">
            <h5 class="card-title">{{ f.title }}</h5>
            <p class="card-text">{{ f.desc }}</p>
          </div>
                    <!-- Button trigger modal -->
          <button type="button" class="btn btn-danger w-50 text-center fw-bold" data-bs-toggle="modal" data-bs-target="#exampleModal">
            Szavazatok
          </button>
          <!-- Modal -->
          <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog">
              <div class="modal-content">
                <div class="modal-header">
                  <h5 class="modal-title" id="exampleModalLabel">Itt tudsz szavazni</h5>
                  <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                  Star Wars: Egy új remény <button class="btn btn-warning mx-1" @click="incrisesw">+</button> 
                  <span class="fw-bold">Összes szavazat : {{ votessw }}</span>
                </div>
                <div class="modal-body">
                  A marsi <button class="btn btn-warning mx-1" @click="incrisem">+</button> 
                  <span class="fw-bold">Összes szavazat : {{ votesm }}</span>
                </div>
                <div class="modal-body">
                  2001: Űrodüsszeia <button class="btn btn-warning mx-1" @click="incrises">+</button> 
                  <span class="fw-bold">Összes szavazat : {{ votess }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
 </div>
</template>

