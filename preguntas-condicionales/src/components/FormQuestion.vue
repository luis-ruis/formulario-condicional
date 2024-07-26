<template>
  <div v-if="isVisible">
    <label :for="question.id">{{ question.label }}</label>
    <component
      :is="question.type === 'input' ? 'input' : 'select'"
      v-bind="componentProps"
      @input="onInput"
      @change="onChange"
    >
      <option v-for="option in question.options" :key="option.value" :value="option.value">
        {{ option.label }}
      </option>
    </component>
  </div>
</template>

<script>
import { defineComponent, computed, toRefs } from 'vue';

export default defineComponent({
  name: 'FormQuestion',
  props: {
    question: Object,
    answers: Object,
    setAnswer: Function
  },
  setup(props) {
    const { question, answers } = toRefs(props);

    const isVisible = computed(() => {
      if (question.value.dependencies.length === 0) return true;
      return question.value.dependencies.some(dep => 
        answers.value[dep.questionId] === dep.value
      );
    });

    const componentProps = computed(() => {
      if (question.value.type === 'input') {
        return {
          type: 'text',
          id: question.value.id,
          value: answers.value[question.value.id] || ''
        };
      } else if (question.value.type === 'select') {
        return {
          id: question.value.id,
          value: answers.value[question.value.id] || ''
        };
      }
      return {};
    });

    const onInput = (event) => {
      props.setAnswer(question.value.id, event.target.value);
    };

    const onChange = (event) => {
      props.setAnswer(question.value.id, event.target.value);
    };

    return {
      isVisible,
      componentProps,
      onInput,
      onChange
    };
  }
});
</script>

<style scoped>
/* Add your styles here */
</style>
