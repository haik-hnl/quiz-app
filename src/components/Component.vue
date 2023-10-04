<template></template>

<script setup lang="ts">
import { ref } from "vue";

const questions = ref([
  {
    question: "Warum ist Aki so ein Huen?",
    answer: 0,
    options: ["Schlecht in LoL", "Arsch in Rl", "No aim", "Kleine Banane"],
    selected: null,
  },
  {
    question: "Warum ist Aki so ein Huen?",
    answer: 0,
    options: ["Schlecht in LoL", "Arsch in Rl", "No aim", "Kleine Banane"],
    selected: null,
  },
  {
    question: "Warum ist Aki so ein Huen?",
    answer: 0,
    options: ["Schlecht in LoL", "Arsch in Rl", "No aim", "Kleine Banane"],
    selected: null,
  },
]);

const quizCompleted = ref(false);
const currentQuestion = ref(0);
const score = computed(() => {});
</script>
<style scoped></style>
