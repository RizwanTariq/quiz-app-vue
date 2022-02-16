<template>
  <div class="questions-ctr">
    <div class="progress">
      <div
        class="bar"
        :style="{ width: `${(qAnswered / questions.length) * 100}%` }"
      ></div>
      <div class="status">{{ qAnswered + 1 }} out of 3 questions answered</div>
    </div>
    <div
      class="single-question"
      v-for="(question, qIndex) in questions"
      :key="question.q"
      v-show="qIndex == qAnswered"
    >
      <div class="question">{{ question.q }}</div>
      <div
        class="answers"
        v-for="answer in question.answers"
        :key="answer.text"
        @click.prevent="selectAnswer(answer.is_correct)"
      >
        <div class="answer">{{ answer.text }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Questions",
  props: {
    questions: {
      type: Array,
      required: true,
    },
    qAnswered: {
      type: Number,
    },
  },
  emits: ["question-answered"],
  methods: {
    selectAnswer(answer) {
      this.$emit("question-answered", answer);
    },
  },
};
</script>

<style></style>
