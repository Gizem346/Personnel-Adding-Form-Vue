<script setup>

const props = defineProps(['personels'])
console.log(props)

const deleteCard = (index) => {
  props.personels.splice(index,1);
}

</script>

<template>

  <h2 class="m-5 list-header">Personnel List</h2>

  <div class="row row-cols-1 row-cols-md-5 g-1 p-5 my-4">
    <div v-for="(person, index) in props.personels" :key="person.index" class="col">
      <div class="card shadow p-3 mb-5 bg-body rounded">
        <img :src=person.image alt="personnel-img" class="card-img-top card-img">
        <div class="card-body text-dark">
          <h5 class="card-title">{{person.name}} {{person.surname}}</h5>
          <h6 class="card-text">{{person.title}}</h6>
          <p class="card-text">{{person.gender}}</p>
        </div>
        <div class="d-grid gap-2 d-md-flex justify-content-center">
          <button @click="deleteCard(index)" type="button" class="btn btn-outline-danger mb-3">Delete</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.list-header {
  background-color: #F98800 !important;
  color: #353F58 !important;
  text-align: center;
}
</style>
