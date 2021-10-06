<template lang="html">
  <section class="button">
    <button @click="buttonClickAction" type="button" :value="buttonValue.id" :disabled='buttonValue.isDisable'  ><div v-html="buttonValue.icon"></div></button>
  </section>
</template>

<script lang="js">
export default {
  props: ["buttonValue"],
  methods: {
    buttonClickAction() {
      this.$emit("onClick");
    },
  },
};
</script>

<style scoped lang="css">
button {
  height: 50px;
  width: 50px;
  margin: 5px;
}
</style>