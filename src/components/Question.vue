<!-- @format -->
<script setup>
import { defineProps, defineEmits } from "vue";

const emit = defineEmits(["selectOption"]);
const { question } = defineProps(["question"]);
// console.log(question);

const emitSelectedOption = (isCorrect) => {
  emit("selectOption", isCorrect);
};
</script>
<template>
  <div class="question-container">
    <h1 class="question">{{ question.text }}</h1>
  </div>
  <div class="options-container">
    <div
      @click="emitSelectedOption(option.isCorrect)"
      v-for="option in question.options"
      :key="option.id"
      class="option"
    >
      <p class="option-label">{{ option.label }}</p>
      <div class="option-value">p{{ option.text }}</div>
    </div>
  </div>
</template>

<style scoped>
.question-container {
  margin-top: 20px;
}

.question {
  font-size: 40px;
  margin-bottom: 20px;
}
.option {
  display: flex;
  align-items: center;
  justify-content: center;
  /* margin-bottom: 20px; */
  cursor: pointer;
}

.option-label {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50px;
  height: 50px;
  font-size: 30px;
  background-color: bisque;
}

.option-value {
  background-color: rgb(224, 239, 239);
  width: 100%;
  font-size: 42px;
  padding: 0 20px;
  display: flex;
  align-items: center;
}
</style>
