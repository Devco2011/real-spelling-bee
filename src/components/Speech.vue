<template>
  <div>
    <button @click="sayWord">Say Word</button>
  </div>
</template>

<script>
export default {
  props: ["word"],

  methods: {
    sayWord() {
      const utterance = new SpeechSynthesisUtterance(this.word);
      speechSynthesis.speak(utterance);
    },
  },
};
</script>

<style>
</style>