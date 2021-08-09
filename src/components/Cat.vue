<template>
  <button class="button" @click="loadNextImage">Next</button>
  <div class="cat">
    <img :src="image.url">
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import axios from 'axios';

@Options({
  data () {
    return {
      image: {
        url: null
      }
    }
  },
  created () {
      this.loadNextImage();
  },
  methods: {
    async loadNextImage() {
        try {
            axios.defaults.headers.common['x-api-key'] = "DEMO-API-KEY"
            let response = await axios.get('https://api.thecatapi.com/v1/images/search', { params: { limit:1, size:"full" } } )
            this.image = response.data[0]
        } catch(err) {
            console.log(err)
        }
    },
  }
})

export default class Cat extends Vue {}
</script>

<style>
.button {
  border-radius: 0px;
  margin: 25px 5px 20px 20px;
  padding: 15px;
  cursor: pointer;
  background-color: #0378d5;
  border-color: transparent;
  color: #fff;
  text-align: center;
}

.cat img {
  width: 100vh;
}
</style>