<template>
  <h2>{{ title }}</h2>
  <myImage :image="image"></myImage>

  <div class="buttonDiv">
    <buttonTimer v-on:onClick="Play" :buttonValue="listButtons[0]"></buttonTimer>
    <buttonTimer v-on:onClick="Pause" :buttonValue="listButtons[1]"></buttonTimer>
    <buttonTimer v-on:onClick="Stop" :buttonValue="listButtons[2]"></buttonTimer>
  </div>

  <p>{{ state }}</p>
  <timer></timer>
  <p>{{ timer }}</p>
</template>

<script>
import buttonTimer from "./components/Button.vue";
import myImage from "./components/Image.vue";
import timer from "./components/Timer.vue";

export default {
  name: "App",
  components: {
    buttonTimer,
    myImage,
    timer
  },
  data() {
    return {
      title: "Pomodoro : Ben & Jerry",
      state: "WORK !",
      timer: "0.0",
      image: require("./assets/tomate2.jpg"),
      listButtons: [
        {
          id: "buttonPlay",
          icon: '<i class="fas fa-play"></i>',
          isDisable: false,
        },
        {
          id: "buttonPause",
          icon: '<i class="fas fa-pause"></i>',
          isDisable: true,
        },
        {
          id: "buttonStop",
          icon: '<i class="fas fa-stop"></i>',
          isDisable: true,
        },
      ],
    };
  },
  methods: {
    Play() {
      this.listButtons[0].isDisable = true;
      this.listButtons[1].isDisable = false;
      this.listButtons[2].isDisable = false;
    },
    Pause() {
      this.listButtons[0].isDisable = false;
      this.listButtons[1].isDisable = true;
      this.listButtons[2].isDisable = false;
    },
    Stop() {
      this.listButtons[0].isDisable = false;
      this.listButtons[1].isDisable = true;
      this.listButtons[2].isDisable = true;
    },
    SwitchState(state) {
      if (state == "WORK !") {
        state = "REST !";
      } else {
        state = "WORK !";
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.buttonDiv {
  display: flex;
  justify-content: center;
}
</style>
