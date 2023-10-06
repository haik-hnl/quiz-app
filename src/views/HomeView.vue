<template></template>

<script setup lang="ts">
import { ref } from "vue";
import Question from "../module/Question";

const questions = ref([
  {
    question: "Test",
    answer: 0,
    options: ["AntwortA", "AntwortB", "AntwortC"],
    selected: null,
  },
  {
    question: "Test",
    answer: 0,
    options: ["AntwortA", "AntwortB", "AntwortC"],
    selected: null,
  },
  {
    question: "Test",
    answer: 0,
    options: ["AntwortA", "AntwortB", "AntwortC"],
    selected: null,
  },
]);

</script>
