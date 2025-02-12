<template>
  <div class="modal">
    <div class="modal_overlay">
      <div class="modal_container">
        <button @click="close" class="modal_close">✖</button>

        <slot name="header">
          <h1 class="modal_title">{{ parentMessage }}</h1>
        </slot>

        <slot name="main">
          <textForModal />
          <div class="modal_footer">
            <button @click="close" class="modal_button">OK</button>
          </div>
        </slot>

        <slot name="footer"></slot>
      </div>
    </div>
  </div>
</template>

<script>
import textForModal from "./textForModal.vue";

export default {
  components: { textForModal },
  emits: ["close"],
  props: {
    parentMessage: String,
  },
  methods: {
    close() {
      this.$emit("close");
    }
  }
};
</script>

<style scoped>
/* Затемненный фон */
.modal_overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Контейнер модального окна */
.modal_container {
  width: 700px;
  height: 400px;
  background: white;
  position: relative;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

/* Заголовок */
.modal_title {
  display: flex;
  justify-content: center;
  color: black;
  font-weight: bold;
}

/* Кнопка закрытия */
.modal_close {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 18px;
  cursor: pointer;
}

/* Подвал модального окна */
.modal_footer {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 45px;
}

/* Кнопка */
.modal_button {
  background: linear-gradient(135deg, #007bff, #0056b3);
  color: white;
  font-size: 18px;
  font-weight: bold;
  border: none;
  padding: 12px 24px;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.modal_button:hover {
  background: linear-gradient(135deg, #0056b3, #003580);
  transform: scale(1.05);
}

.modal_button:active {
  transform: scale(0.98);
}
</style>
