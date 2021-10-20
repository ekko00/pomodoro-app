<template lang="html">

  <section class="rest">
    <img :src="this.restImage">
  </section>

</template>

<script lang="js">
  import axios from 'axios'
  import stopImage from "../assets/stop.jpg"
  import loadingImage from "../assets/loading.gif"

  export default  {
    name: 'rest',
    props: [],
    mounted () {

    },
    data () {
      return {
        // variable associated with src attribut from img html tag (in template)
        restImage: String
      }
    },
    created (){
      this.showStop();
    },
    methods: {
      async showCat() {
        this.restImage = loadingImage;
        try{
          // Create header for ajax get call
          axios.defaults.headers.common['x-api-key'] = "d1d82d47-9b7b-47e1-88a2-d5356ef04279";

          // Wait for the request response
          let response = await axios.get('https://api.thecatapi.com/v1/images/search', { params: { limit:1, size:"full" } } );

          // Save image url in restImage
          this.restImage = response.data[0].url;
        }
        catch(err) {
          console.log(err);
        }
      },

      showStop() {
        // Save stop image url in restImage
        this.restImage = stopImage;
      }

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  section.rest{
    background-color: white;
    height: 400px;
    margin-left: 30%;
    margin-right: 30%;
  }

  section.rest>img{
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
</style>
