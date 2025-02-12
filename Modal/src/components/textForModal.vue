<template>
  <div class="block">
    <div class="block_question">{{ firstQuestion }}</div>
    <input v-model="appState.infoTextOne" class="block_input" type="text">
    
    <div class="block_question">{{ secondQuestion }}</div>
    <input v-model="appState.infoTextTwo" class="block_input" type="text">
  </div>
</template>

<script>
export default {
  inject: ["appState"],
  data() {
    return {
      firstQuestion: "What is your favorite film?",
      secondQuestion: "What is your favorite actor?",
    };
  }
};
</script>

<style scoped>
.block {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.block_question {
  color: black;
  font-size: 23px;
}

.block_input {
  color: black;
  font-size: 23px;
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 5px;
  outline: none;
}

.block_input:focus {
  border-color: #007bff;
}
</style>
