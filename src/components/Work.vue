<template lang="html">

  <section class="work">
    <img :src="workImage">
  </section>

</template>

<script lang="js">
  import pomodoroImage from "../assets/tomate.png"

  export default {
    name: 'work',
    props: [],
    mounted () {

    },
    data () {
      return {
        workImage: String
      }
    },
    created () {
      this.showPomodoro();
    },
    methods: {

      showPomodoro() {
        this.workImage = pomodoroImage;
      }
    },
    computed: {

    }
  };
</script>

<style scoped lang="css">

img {
  width: 200px;
  margin-top: 10px;
  margin-bottom: 30px;
}

</style>