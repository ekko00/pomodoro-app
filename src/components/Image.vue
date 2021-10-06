<template lang="html">
  <section class="image">
      <img :src="image">
  </section>
</template>

<script lang="js">
export default {
  props: ["image"],
};
</script>

<style scoped lang="css">

img {
  width: 200px;
}

</style>