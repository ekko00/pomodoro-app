<template lang="html">

  <section class="timer">
    <h1>timer Component</h1>
  </section>

</template>

<script lang="js">
  const WORK_TIME_DEFAULT = 1200;
  const REST_TIME_DEFAULT = 300;
  const STATE_DEFAULT = "work";

  export default  {
    name: 'timer',
    props: [],
    mounted () {
      state = STATE_DEFAULT;
      if (state = "work") {
        time = WORK_TIME_DEFAULT;
      }
      else {
        time = REST_TIME_DEFAULT;
      }
    },
    data () {
      return {
        clock: Number;
        time: Number;
        state: String;
      }
    },
    methods: {
      clockProcess() {
        // If the count down is over, write some text 
        if (time <= 0) {
          swapState();
        }
        else {
          decrementTime();
        }
      
        // Show time
        showTime();
      }

      playTimer() {
        clock = setInterval(clockProcess, 1000);
      }

      pauseTimer() {
        clearInterval(clock);
      }

      stopTimer() {
        clearInterval(clock);
        time = workTime;
        state = "work";
      }
      
      showTime() {
        // Time calculations for minutes and seconds
        var minutes = Math.floor((time % (60 * 60)) / 60);
        var seconds = Math.floor((time % (60)));
      }

      decrementTime() {
        time--;
      }

      swapState() {
        if (state == "work") {
          time = restTime;
          state == "rest";
        }
        else {
          time = workTime;
          state = "work";
        }
      }

    },
    computed: {

    }
}


</script>

<style scoped lang="scss">

</style>
