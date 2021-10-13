<template lang="html">

  <section class="timer">
    <h1>{{ state=="work"?"WORK !":"REST !" }}</h1>
    <h1>{{ minutes.toLocaleString('en-US', {minimumIntegerDigits: 2, useGrouping: false }) }}:{{ seconds.toLocaleString('en-US', {minimumIntegerDigits: 2, useGrouping: false }) }}</h1>
  </section>

</template>

<script lang="js">
  const WORK_TIME_DEFAULT = 5; // 1200 = 20 minutes
  const REST_TIME_DEFAULT = 30; // 300 = 5 minutes
  const CAT_RESET_TIME_DEFAULT = 5;
  const STATE_DEFAULT = "work";

  export default  {
    name: 'timer',
    props: [],
    mounted () {
      this.state = STATE_DEFAULT;
      if (this.state == "work") {
        this.time = WORK_TIME_DEFAULT;
      }
      else {
        this.time = REST_TIME_DEFAULT;

      }
      this.showTime();
    },
    data () {
      return {
        clock: Number,
        time: Number,
        state: String,
        minutes: Number,
        seconds: Number
      }
    },
    methods: {
      clockProcess() {
        // If the count down is over, swap state
        if (this.time <= 0) {
          this.swapState();
        }
        else {
          this.decrementTime();

          if (this.state == "rest") {
            this.showAnotherCat();
          }
        }
      
        // Show time
        this.showTime();
      },

      playTimer() {
        this.clock = setInterval(this.clockProcess, 1000);
      },

      pauseTimer() {
        clearInterval(this.clock);
      },

      stopTimer() {
        clearInterval(this.clock);
        this.time = WORK_TIME_DEFAULT;
        this.state = "work";
        this.showTime();
      },
      
      showTime() {
        // Time calculations for minutes and seconds
        this.minutes = Math.floor((this.time % (60 * 60)) / 60);
        this.seconds = Math.floor((this.time % (60)));
      },

      decrementTime() {
        this.time--;
      },

      swapState() {
        if (this.state == "work") {
          this.time = REST_TIME_DEFAULT;
          this.state = "rest";
        }
        else {
          this.time = WORK_TIME_DEFAULT;
          this.state = "work";
        }
        this.showTime();
        this.$emit("swapState", this.state);
      },

      showAnotherCat() {
        if (this.state == "rest" && this.time % CAT_RESET_TIME_DEFAULT == 0) {
          this.$emit("showAnotherCat");
        }
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">

</style>
