<script>
import Slide from "./components/Slide.vue";
export default {
  components: {
    Slide,
  },
  data: () => {
    return {
      slides: [
        {
          id: 1,
          title: "Slide 1",
          description: "This is slide 1",
        },
        {
          id: 2,
          title: "Slide 2",
          description: "This is slide 2",
        },
        {
          id: 3,
          title: "Slide 3",
          description: "This is slide 3",
        },
        {
          id: 4,
          title: "Slide 4",
          description: "This is slide 4",
        },
        {
          id: 5,
          title: "Slide 5",
          description: "This is slide 5",
        },
        {
          id: 6,
          title: "Slide 6",
          description: "This is slide 6",
        },
      ],
      index: 0,
    };
  },
  methods: {
    onForward() {
      if (this.index == 5) {
        this.index = this.index * 0;
      } else {
        this.index = this.index + 1;
      }
    },
    onBack() {
      if (this.index == 0) {
        this.index = this.index + 5;
      } else {
        this.index = this.index - 1;
      }
    },
  },
};
</script>

<template>
  <div class="container">
    <Slide
      :key="slides[index].id"
      :title="slides[index].title"
      :description="slides[index].description"
    />
    <div class="buttons">
      <button @click="onBack(index)">Назад</button>
      <button @click="onForward(index)">Вперед</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 900px;
  height: 500px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  justify-content: center;
}

.buttons {
  display: flex;
  gap: 10px;
}
</style>
