<template>
  <header>
    <div class="block">
      <button class="btn" @click="isModelOpen = true">Open</button>
    </div>

    <modal v-if="isModelOpen" :parentMessage="parentMessage" @close="isModelOpen = false" />

    <div class="info_container" v-if="!isModelOpen">
      <div class="info_message" v-if="hasText">
        <div v-if="infoTextOne">Your favorite film - {{ infoTextOne }}</div>
        <div v-if="infoTextTwo">Your favorite actor - {{ infoTextTwo }}</div>
      </div>
    </div>
  </header>
</template>

<script>
import modal from "./components/modal.vue";

export default {
  components: { modal },
  data() {
    return {
      isModelOpen: false,
      parentMessage: "Say me true😡",
      infoTextOne: "",
      infoTextTwo: ""
    };
  },
  computed: {
    hasText() {
      return this.infoTextOne || this.infoTextTwo;
    }
  },
  provide() {
    return {
      appState: this
    };
  }
};
</script>

<style scoped>
.block {
  display: flex;
  align-items: center;
  justify-content: center;
}
.btn {
  padding: 40px;
  font-size: 30px;
  border-radius: 30px;
  background-color: red;
  color: white;
  border: none;
  cursor: pointer;
}
.info_container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 15px;
}
.info_message {
  bottom: 10px;
  color: white;
  font-size: 18px;
  background: rgba(0, 0, 0, 0.5);
  padding: 10px;
  border-radius: 5px;
}
</style>
