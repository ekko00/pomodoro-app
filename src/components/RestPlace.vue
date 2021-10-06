<template lang="html">

  <section class="rest-place">
    <h1>Cats !</h1>
  </section>

</template>

<script lang="js">
  import axios from 'axios'

  export default  {
    name: 'rest-place',
    props: [],
    mounted () {

    },
    data () {
      return {
        image: { url: ""}
      }
    },
    created() {
      this.loadNextImage();
    },
    methods: {
      async loadRandomCat() {
        try{
          axios.defaults.headers.common['x-api-key'] = "d1d82d47-9b7b-47e1-88a2-d5356ef04279"; // Replace this with your API Key

          let response = await axios.get('https://api.thecatapi.com/v1/images/search', { params: { limit:1, size:"full" } } ); // Ask for 1 Image, at full resolution

          this.image = response.data[0]; // the response is an Array, so just use the first item as the Image

          console.log("-- Image from TheCatAPI.com");
          console.log("id:", this.image.id);
          console.log("url:", this.image.url);

        }
        catch(err) {
          console.log(err);
        }
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="scss">

</style>
