<template>
  <div class="App" >
    <profile-form
    :name="name"
    :age="age"
    :employment="employment"
    :avatar="avatar"/>
    <beer-form
    :beerBrand="beerBrand"
    :beerName="beerName"
    :alcohol="alcohol"
    :getBear="getBear"/>
  </div>
</template>

<script>
import axios from 'axios'
import ProfileForm from "@/components/ProfileForm.vue"
import BeerForm from "@/components/BeerForm.vue"
export default {
  components: {
    ProfileForm, BeerForm
  },
  data() {
    return {
      name: '',
      age: '',
      employment: '',
      avatar: '',
      beerName: '',
      beerBrand: '',
      alcohol: ''
    }
  },
  mounted() {
    axios
      .get('https://random-data-api.com/api/users/random_user')
      .then((response) => {
        const age = response.data.date_of_birth.split('-')
        const date = new Date()
        const now = date.getFullYear()
        this.name = response.data.first_name
        this.age = (now - age[0])
        this.employment = response.data.employment.title
        this.avatar = response.data.avatar
      })
      .catch((e) => {
        console.log(e)
      })
    axios 
      .get('https://random-data-api.com/api/beer/random_beer')
      .then((response) => {
        this.beerName = response.data.name
        this.beerBrand = response.data.brand
        this.alcohol = response.data.alcohol
      })
      .catch((e) => {
        console.log(e)
      })
  },
  methods: {
    async getBear() {
      try {
        const response = await axios.get('https://random-data-api.com/api/beer/random_beer')
        this.beerName = response.data.name
        this.beerBrand = response.data.brand
        this.alcohol = response.data.alcohol
      }
      catch (e) {
        console.log(e)
    }
    }
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.App {
 width: 80vw;
 height: 80vh;
 margin: auto;
 margin-top: 60px;
 border: 1px solid #c2c2c2;
 background-color: white;
 border-radius: 8px;
}

@media screen and (max-width: 1000px) {
  .App {
    margin-top: 30px;
  }
}
@media screen and (max-width: 650px) {
  .App {
  width: 90vw;
  height: 90vh;
  }
}

</style>
