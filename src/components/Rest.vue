<template lang="html">

  <section class="rest">
    <img :src="restImage">
  </section>

</template>

<script lang="js">
  import axios from 'axios'
  import stopImage from "../assets/stop.png"
  import loadingImage from "../assets/loading.gif"

  export default  {
    name: 'rest',
    props: [],
    mounted () {

    },
    data () {
      return {
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
          axios.defaults.headers.common['x-api-key'] = "d1d82d47-9b7b-47e1-88a2-d5356ef04279";

          let response = await axios.get('https://api.thecatapi.com/v1/images/search', { params: { limit:1, size:"full" } } ); // Ask for 1 Image, at full resolution

          this.restImage = response.data[0].url; // the response is an Array, so just use the first item as the Image
        }
        catch(err) {
          console.log(err);
        }
      },

      showStop() {
        this.restImage = stopImage;
      }

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  section.rest{
    border: grey 1px solid;
    background-color: silver;
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
