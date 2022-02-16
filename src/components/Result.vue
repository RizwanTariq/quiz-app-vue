<template>
  <div class="result">
    <div class="title">You got {{ acAnswers }} out of {{ totalQ }}!</div>
    <div class="desc">{{ desc }}</div>
  </div>
</template>

<script>
export default {
  name: "Result",
  props: ["acAnswers", "totalQ"],

  computed: {
    desc() {
      if (this.acAnswers < this.totalQ) {
        return "Do a little more studying and you may succeed!";
      }
      return "Studying has definitely paid off for you!";
    },
  },
};
</script>

<style></style>
