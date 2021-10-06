<template lang="html">
  <section class="image">
      <img :src="image">
  </section>
</template>

<script>
export default {
  props: ["image"],
};
</script>

<style scoped>

img {
  width: 200px;
}

</style>