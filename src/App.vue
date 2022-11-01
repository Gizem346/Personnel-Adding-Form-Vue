<script setup>
import Cards from './components/Cards.vue'
import Navbar from './components/Navbar.vue'

import { ref, reactive } from 'vue';

const name = ref("")
const surname = ref("")
const title = ref("")
const image = ref("")
const gender = ref(null)

let form = reactive({
  name: name.value,
  surname: surname.value,
  title: title.value,
  gender: gender.value,
  image: image.value
})

var formList = reactive([])

const onSubmit = () => {
  const items = reactive({
    name: name.value,
    surname: surname.value,
    title: title.value,
    gender: gender.value,
    image: image.value
  })
  formList.push(items)
  console.log(formList)

  name.value = ""
  surname.value = ""
  title.value = ""
  gender.value = null
  image.value = ""
}

</script>

<template>
  <div class="App">
    <Navbar />

      <div id="form" class="container-fluid d-flex justify-content-center border form-container field">
        <form class="my-5 p-5 text-white" @submit.prevent="onSubmit">
          <h2>Personnel Adding Form</h2>

          <div class="input-group mb-3">
            <label>Name
              <input v-model.lazy="name" type="text" class="form-control" required>
            </label>
          </div>

          <div class="input-group mb-3">
            <label>Surname
              <input v-model.lazy="surname" type="text" class="form-control" required>
            </label>
          </div>

          <div class="input-group mb-3">
            <label>Title
              <input v-model.lazy="title" type="text" class="form-control" required>
            </label>
          </div>

          <div class="form-check">
            <input type="radio" v-model="gender" class="form-check-input" name="radio-btn-gender" id="male"
              value="Male">
            <label for="male" class="form-check-label">Male</label>
          </div>

          <div class="form-check">
            <input type="radio" v-model="gender" class="form-check-input" name="radio-btn-gender" id="female"
              value="Female">
            <label for="female" class="form-check-label">Female</label>
          </div>

          <div class="form-check mb-3">
            <input type="radio" v-model="gender" class="form-check-input" name="radio-btn-gender" id="other"
              value="Other">
            <label for="other" class="form-check-label">Other</label>
          </div>

          <div class="input-group mb-3">
            <input type="text" v-model="image" class="form-control" id="choose-pphoto" placeholder="Add your photo url" required>
            <label for="choose-photo" class="input-group-text">Profile Photo</label>
          </div>

          <div class="d-grid gap-2 col-6 mx-auto">
            <button @click="" type="submit" class="btn btn-outline-success mt-5">Submit</button>
          </div>

        </form>
      </div>

    <div>
      <Cards :personels="formList"/>
    </div>
  </div>
</template>

<style scoped>
.field {
    background: url("https://images.pexels.com/photos/3184291/pexels-photo-3184291.jpeg?auto=compress&cs=tinysrgb&w=1600")center/cover;
}
form{
    background-color: rgba(0, 0, 0, 0.7);
}
.list-header{
  background-color: #F98800!important;
  color: #353F58!important;
  text-align: center;
}
</style>
