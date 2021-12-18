<template>
  <div>
      <div class="container p-4">
          <div class="row">
              <div class="col-md-4 col-sm-12 col-lg-4 col-xl-4 col-xxl-4 mt-4" v-for="character in charactersData.slice(0, 10)" :key="character.id">
                  <div class="card shadow-lg">
                      <img :src="character.imageUrl" :alt="character.imageUrl" class="card-fluid card-img-top">
                      <div class="card-body">
                          <h5 class="card-title">
                              {{ character.name }}
                          </h5>
                      </div>
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
    created() {
        this.getAllCharacters();
    },

    data() {
        return {
            charactersData: [],
        }
    },

    methods: {
        getAllCharacters() {
            return axios.get('http://api.disneyapi.dev/characters')
                .then(response => {
                    console.log(response);
                    this.charactersData = response.data.data;
                })
                .chatch(error => {
                    console.error(error);
                })
        }
    }
}
</script>

<style scoped>

</style>