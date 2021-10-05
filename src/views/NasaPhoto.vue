<template>
  <div id="photo" class="photo">
    <div class="container">
      <div class="photoWrap">
          <h1>{{ photo.title }}</h1>
          <h3>{{ photo.date }}</h3>
          <img v-bind:src="photo.url" />
          <p>{{ photo.explanation }}</p>
        </div>
    </div>
  </div>
</template>

<script>
import Axios from "axios";
export default {
  name: "NasaPhoto",
  data() {
    return {
      apiKey: process.env.VUE_APP_APIKEY,
      photo: "",
    };
  },
  created() {
    Axios.get(
      `https://api.nasa.gov/planetary/apod?api_key=${this.apiKey}&date=2017-08-07`
    ).then((response) => {
      if (response.data.error) {
        return;
      } else {
        this.photo = response.data;

      }
    });
  },
};
</script>

<style scoped>
img {
  width: 500px;
}
</style>
