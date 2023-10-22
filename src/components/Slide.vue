<script>
export default {
  props: ["title", "description"],
  data: () => {
    return {};
  },
};
</script>

<template>
  <div class="slide">
    <h1>{{ title }}</h1>
    <h3>{{ description }}</h3>
  </div>
</template>

<style scoped>
.slide {
  width: 500px;
  height: 300px;
  border: 1px solid black;
  color: black;
  gap: 5px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
