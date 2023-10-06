<template>
  <div>
    <h1> {{ currentQuestion.question }} </h1>
    <ul>
      <li v-for="option in currentQuestion.options" :key="options.id">
        <button @click=""> {{  }} </button>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Question from "../module/Question";

const questions: Question[] = [
  {
    id: 1,
    question: "test",
    options: [
      { id: 1, text: "option1", isCorrect: true },
      { id: 2, text: "option2", isCorrect: false },
      { id: 3, text: "option3", isCorrect: false }
    ]
  },
];

const allQuestions = questions.length
const currentQuestion = ref(questions[0]);
const currentIndex = ref(0);

const selectQuestion = () => {
  if (currentIndex.value < allQuestions - 1) {
    currentIndex.value ++;
    currentQuestion.value = questions[currentIndex.value];
  }
};
</script>
