<template>
  <div>
    <FormQuestion
      v-for="question in questions"
      :key="question.id"
      :question="question"
      :answers="answers"
      :setAnswer="setAnswer"
    />
  </div>
</template>

<script>
import { defineComponent, reactive } from 'vue';
import FormQuestion from './components/FormQuestion.vue';
import formConfig from './form-config.json';

export default defineComponent({
  name: 'App',
  components: { FormQuestion },
  setup() {
    const questions = formConfig.questions;
    const answers = reactive({});

    const setAnswer = (questionId, value) => {
      answers[questionId] = value;
    };

    return {
      questions,
      answers,
      setAnswer
    };
  }
});
</script>

<style>
/* Add your styles here */
</style>
