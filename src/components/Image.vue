<template>
  <div>
      <img :src="image">
  </div>
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