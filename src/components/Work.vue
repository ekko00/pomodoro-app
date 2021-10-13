<template lang="html">

  <section class="work">
    <img :src="workImage">
  </section>

</template>

<script lang="js">
  import pomodoroImage from "../assets/tomate.jpg"

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
}

</style>