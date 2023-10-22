<script>
export default {
  props: ["percent", "job", "id"],
  data: () => {
    return {
      jobValue: "",
      percentValue: 0,
      colored_percent: 0,
    };
  },
  methods: {
    onClick() {
      this.$emit("changeBlock", this.id, this.percentValue, this.jobValue);
      this.percentValue = "";
      this.jobValue = "";
    },
  },
};
</script>

<template>
  <div class="block">
    <input type="text" placeholder="Что-то" v-model="jobValue" />
    <input
      type="number"
      min="0"
      max="100"
      placeholder="Процент"
      v-model="percentValue"
    />
    <button
      @click="onClick"
      :disabled="
        !jobValue || !percentValue || percentValue > 100 || percentValue < 0
      "
    >
      Сохранить
    </button>
    <div class="colored-part">
      <div
        class="colored-part-inner"
        :style="{ height: `${percent}%`, borderTop: '1px solid black' }"
      ></div>
    </div>
    <div class="job-name">{{ job }}</div>
  </div>
</template>

<style scoped>
.block {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.colored-part {
  height: 300px;
  border: 1px solid black;
  display: flex;
  align-items: flex-end;
}
.job-name {
  color: black;
  display: flex;
  justify-content: center;
}
.colored-part-inner {
  width: 100%;
  background: yellow;
}
</style>
