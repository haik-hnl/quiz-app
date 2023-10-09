<template>
  <div>
    <h1>{{ currentQuestion.question }}</h1>
    <ul>
      <li v-for="option in currentQuestion.options" :key="option.id">
        <button @click="selectQuestion">{{ option.id }}</button>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Question from "../model/Question";

const questions: Question[] = [
  {
    id: 1,
    question: "asdfghj",
    options: [
      { id: 1, text: "option1", isCorrect: true },
      { id: 2, text: "option2", isCorrect: false },
      { id: 3, text: "option3", isCorrect: false },
    ],
  },
  {
    id: 2,
    question: "test1",
    options: [
      { id: 1, text: "option1", isCorrect: true },
      { id: 2, text: "option2", isCorrect: false },
      { id: 3, text: "option3", isCorrect: false },
    ],
  },
  {
    id: 3,
    question: "test2",
    options: [
      { id: 1, text: "option1", isCorrect: true },
      { id: 2, text: "option2", isCorrect: false },
      { id: 3, text: "option3", isCorrect: false },
    ],
  },
  {
    id: 4,
    question: "test3",
    options: [
      { id: 1, text: "option1", isCorrect: true },
      { id: 2, text: "option2", isCorrect: false },
      { id: 3, text: "option3", isCorrect: false },
    ],
  },
  {
    id: 5,
    question: "test4",
    options: [
      { id: 1, text: "option1", isCorrect: true },
      { id: 2, text: "option2", isCorrect: false },
      { id: 3, text: "option3", isCorrect: false },
    ],
  },
];

const allQuestions = questions.length;
const currentQuestion = ref(questions[0] as Question);
const currentIndex = ref(0);

const selectQuestion = () => {
  if (currentIndex.value < allQuestions - 1) {
    currentIndex.value++;
    currentQuestion.value = questions[currentIndex.value];
  }
};
</script>
