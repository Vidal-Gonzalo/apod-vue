<template>
  <div id="photo" class="photo">
    <div class="photo-wrap container">
      <div v-if="photo">
        <h1>{{ photo.title }}</h1>
        <div class="row">
          <div class="photo-image col-6">
            <div v-if="photo.media_type === 'video'">
              <iframe
                v-bind:src="photo.url"
                alt="Youtube Video"
                frameborder="0"
                allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
                allowfullscreen
              ></iframe>
            </div>
            <div v-else>
              <img v-bind:src="photo.url" class="img-fluid" alt="Image" />
            </div>
            <p>{{ photo.date }}</p>
          </div>
          <div class="photo-explanation col-6">
            <p>{{ photo.explanation }}</p>
          </div>
        </div>
        <div class="row">
          <div class="button-wrap">
            <button @click="goHome" class="btn btn-primary button mt-3">
              Search for another picture <i class="bi bi-camera ms-2"></i>
            </button>
          </div>
        </div>
      </div>
      <div v-else>Loading...</div>
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
  methods: {
    goHome() {
      this.$router.push("/");
    },
  },
  created() {
    this.date = this.$route.params.date;
    Axios.get(
      `https://api.nasa.gov/planetary/apod?api_key=${this.apiKey}&date=${this.date}`
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
.photo {
  background-image: url("~@/assets/nasabackground.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  height: calc(100vh + 50px);
  display: flex;
  align-items: center;
}

.photo-wrap {
  font-family: "Barlow Condensed", sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: #fff;
  background: rgba(26, 2, 30, 0.6);
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.18);
  width: 60vw;
  padding: 20px;
}

.photo-image {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  flex-direction: column;
}

img,
iframe {
  border-radius: 10px;
  max-width: 300px;
}

.photo-explanation {
  max-height: 60vh;
  overflow: auto;
}

.photo-explanation::-webkit-scrollbar {
  -webkit-appearance: none;
}

.photo-explanation::-webkit-scrollbar:vertical {
  width: 10px;
}

.photo-explanation::-webkit-scrollbar-button:increment,
.photo-explanation::-webkit-scrollbar-button {
  display: none;
}

.photo-explanation::-webkit-scrollbar:horizontal {
  height: 10px;
}

.photo-explanation::-webkit-scrollbar-thumb {
  background-color: rgba(26, 2, 30, 0.6);
  border-radius: 20px;
  border: 1px solid #f1f2f3;
}

.button {
  width: 50%;
}

</style>

