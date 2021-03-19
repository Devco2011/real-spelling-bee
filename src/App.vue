<template>
  <div class="container">
    <h1>Spelling Test</h1>
    <speech :word="questions[activeIndex].word" />
    <form @submit.prevent="handleSubmit">
      <input
        type="text"
        spellcheck="false"
        v-model="userInput"
        placeholder="Spell the word"
      />
      <button>Submit</button>
    </form>
  </div>
</template>

<script>
import data from "./data";
import Speech from "./components/Speech";

export default {
  components: { Speech },

  data() {
    return {
      questions: data,
      activeIndex: 0,
      userInput: "",
    };
  },
  methods: {
    handleSubmit() {
      this.questions[this.activeIndex].userInput = this.userInput;
      this.activeIndex += 1;
      this.userInput = "";
    },
  },
  computed: {
    testFinished() {
      return this.questions.every((q) => q.userInput);
    },
  },
};
</script>

<style>
</style>
