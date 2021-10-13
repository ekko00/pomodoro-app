<template lang="html">
  <h2>{{ title }}</h2>
  <work ref="workRef"></work>

  <div class="buttonDiv">
    <actionButtons v-on:onClick="Play" :buttonValue="listButtons[0]"></actionButtons>
    <actionButtons v-on:onClick="Pause" :buttonValue="listButtons[1]"></actionButtons>
    <actionButtons v-on:onClick="Stop" :buttonValue="listButtons[2]"></actionButtons>
  </div>
  
  <timer ref="timerRef" @swapState="UpdateView" @showAnotherCat="UpdateView"></timer>
  
  <rest ref="restRef"></rest>
</template>

<script lang="js">
import ActionButtons from "./components/Button.vue";
import Work from "./components/Work.vue";
import Timer from "./components/Timer.vue";
import Rest from "./components/Rest.vue";

export default {
  name: "App",
  components: {
    ActionButtons,
    Work,
    Timer,
    Rest
  },
  data() {
    return {
      title: "Pomodoro : Luka & Thibaud",
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
      this.$refs.timerRef.playTimer();
    },
    Pause() {
      this.listButtons[0].isDisable = false;
      this.listButtons[1].isDisable = true;
      this.listButtons[2].isDisable = false;
      this.$refs.timerRef.pauseTimer();
      this.$refs.restRef.showStop();
    },
    Stop() {
      this.listButtons[0].isDisable = false;
      this.listButtons[1].isDisable = true;
      this.listButtons[2].isDisable = true;
      this.$refs.timerRef.stopTimer();
      this.$refs.restRef.showStop();
    },
    UpdateView(state){
      if (state == "work") {
        this.$refs.restRef.showStop();
      }
      else {
        this.$refs.restRef.showCat();
      }
    },
  },
};
</script>

<style lang="css">
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
