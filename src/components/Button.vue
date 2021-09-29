<template>
  <div>
    <button @click="buttonClickAction" type="button" :value="buttonValue.id" :disabled='buttonValue.isDisable'  ><div v-html="buttonValue.icon"></div></button>
  </div>
</template>

<script>
export default {
  props: ["buttonValue"],
  methods: {
    buttonClickAction() {
      this.$emit("onClick");
    },
  },
};
</script>

<style scoped>
button {
  height: 50px;
  width: 50px;
  margin: 5px;
}
</style>