<script>
export default {
  data: () => {
    return {
      age: 0,
      colorsList: [],
      textInput: "",
    };
  },
  computed: {
    returnText() {
      return this.textInput;
    },
  },
  mounted() {
    for (let i = 0; i <= 7; i++) {
      const randomRgbColor = () => {
        let r = Math.floor(Math.random() * 256);
        let g = Math.floor(Math.random() * 256);
        let b = Math.floor(Math.random() * 256);
        return "rgb(" + r + "," + g + "," + b + ")";
      };
      this.colorsList.push(randomRgbColor());
    }
  },
};
</script>

<template>
  <div class="task">
    <h2>Второе задание</h2>
    <input type="number" min="-1" max="120" placeholder="Возраст" v-model="age" />
    <p v-if="typeof age == string">Возраст не ясен</p>
    <p v-else-if="age < 18 && age >= 0">Несовершеннолетний</p>
    <p v-else-if="age >= 18 && age < 120">Совершеннолетний</p>
    <p v-else>Неправильный возраст</p>
  </div>

  <div class="task">
    <h2>Третье задание</h2>
    <div class="card" v-for="(color, key) in colorsList" :key="key">
      <div class="card_color-block" :style="{ backgroundColor: color }"></div>
      <!-- НЕ УБИВАЙТЕ, Я НЕ НАШЕЛ РЕШЕНИЕ КРОМЕ КАК ЧЕРЕЗ STYLE !!! -->
      <p>{{ color }}</p>
    </div>
  </div>

  <div class="task">
    <h2>Четвертое задание</h2>
    <input class="top-text" readonly :value="returnText" />
    <textarea v-model="textInput" placeholder="Писать тут..."></textarea>
  </div>
</template>

<style scoped>
.task {
  padding: 10px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 300px;
  align-items: center;
}

.card {
  width: 150px;
  height: 150px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  align-items: center;
  background: wheat;
  color: black;
  justify-content: center;
  border-radius: 15px;
}

.card_color-block {
  width: 70px;
  height: 70px;
}

.top-text {
  font-weight: bold;
  font-style: italic;
}
</style>
