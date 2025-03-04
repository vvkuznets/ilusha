<template>
  <div class="hello">
    <CircleProgressBar :value="value" :max="100" />
    <div>{{ value }} %</div>
  </div>
</template>

<script>
import { CircleProgressBar } from 'vue3-m-circle-progress-bar';

export default {
  name: 'HelloWorld',
  components: {
    CircleProgressBar
  },
  data() {
    return {
      value: 50,
    }
  },
  mounted() {
    // Добавляем обработчик события при монтировании компонента
    window.addEventListener('keyup', this.handleKeyUp);
  },
  beforeUnmount() {
    // Удаляем обработчик события при уничтожении компонента
    window.removeEventListener('keyup', this.handleKeyUp);
  },
  methods: {
    handleKeyUp(event) {
      // Проверяем, была ли нажата клавиша Enter (код 13)
      if (event.key === 'Enter') {
        this.onEnterPressed();
      }
      // Проверяем, была ли нажата клавиша Backspace (код 8 или key === 'Backspace')
      if (event.key === 'Backspace') {
        this.onBackspacePressed();
      }
    },
    onEnterPressed() {
      // Метод, который срабатывает при нажатии Enter
      this.value += 10;
    },
    onBackspacePressed() {
      // Метод, который срабатывает при нажатии Backspace
      this.value -= 10;
    },
  },
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
