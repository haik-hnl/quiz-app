<template>
  <Toast />
  <div v-if="!lastQuestion">
    <h1>{{ currentQuestion.question }}</h1>
    <ul>
      <ul v-for="option in currentQuestion.options" :key="option.id">
        <p>{{ option.text }}</p>
        <button @click="selectQuestion(option.isCorrect)">
          {{ option.id }}
        </button>
      </ul>
    </ul>
  </div>
  <div class="card flex justify-content-center">
    <Dialog
      v-model:visible="visible"
      modal
      header="Congratulations!!!"
      :style="{ width: '50vw' }"
    >
      <p>Restart the game!</p>
      <template #footer>
        <Button
          label="Restart the game!"
          icon="pi pi-check"
          @click="reloadPage()"
          autofocus
        />
      </template>
    </Dialog>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import Question from "../model/Question";
import quizData from "../data/question.json";
import Toast from "primevue/toast";
import { useToast } from "primevue/usetoast";
import Dialog from "primevue/dialog";
import Button from "primevue/button";

const currentQuestion = ref(quizData[0] as Question);
const currentIndex = ref(0);
const toast = useToast();
const visible = ref(false);
const lastQuestion = ref(false);

const selectQuestion = (isCorrect?: boolean) => {
  if (!isCorrect) {
    showError();
    return;
  } else {
    showSuccess();
  }

  if (currentIndex.value <= quizData.length) {
    goToNextQuestion();
  }
  if (currentIndex.value == quizData.length) {
    restartGame();
  }
};

const goToNextQuestion = () => {
  currentIndex.value++;
  currentQuestion.value = quizData[currentIndex.value];
};

const restartGame = () => {
  lastQuestion.value = true;
  visible.value = true;
};

const reloadPage = () => {
  visible.value = false;
  window.location.reload();
};

const showSuccess = () => {
  toast.add({
    severity: "success",
    summary: "Correct answer!",
    detail: "You must be smart! :D",
    life: 3000,
  });
};

const showError = () => {
  toast.add({
    severity: "error",
    summary: "Wrong answer!",
    detail: "Try again!",
    life: 3000,
  });
};
</script>
