<template>
  <div id="home" class="home">
    <div class="home-wrap container">
      <h1>Welcome to SpaceHub</h1>
      <p>Pick a day and we will show you the photo most valorated by NASA!</p>
      <DatePicker
        class="date-picker"
        color="indigo"
        mode="date"
        is-dark
        v-model="selectedDate"
      />
      <p>Note: NASA started rating pictures in 2015</p>
      <button class="btn btn-lg btn-primary">
        Ver foto <span class="material-icons align-center"> east </span>
      </button>
    </div>
  </div>
</template>

<script>
import { DatePicker } from "v-calendar";

export default {
  name: "Home",
  components: {
    DatePicker,
  },
  data() {
    return {
      selectedDate: new Date(),
    };
  },
};
</script>

<style scoped>
.home {
  font-family: "Barlow Condensed", sans-serif;
  background-image: url("~@/assets/spacewallpaper1.jpg");
  background-position: center;
  background-repeat: no-repeat;
  height: 100vh;
  display: flex;
  align-items: center;
}

.home-wrap {
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
  width: 50%;
  padding: 20px;
}

.home-wrap h1 {
  font-size: 3em;
  font-weight: bold;
}

.home-wrap p {
  font-weight: light;
}

.home-wrap button {
  display: flex;
  justify-content: center;
  align-items: center;
}

.home-wrap button span {
  margin-top: 5px;
  margin-left: 8px;
}

.date-picker {
  width: 30vw;
  height: 45vh;
}
</style>
