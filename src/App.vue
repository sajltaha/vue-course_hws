<script>
import InfoBlock from "./components/InfoBlock.vue";
export default {
  components: {
    InfoBlock,
  },
  data: () => {
    return {
      containers: [
        {
          id: 1,
          percent: 0,
          job: "",
        },
        {
          id: 2,
          percent: 0,
          job: "",
        },
        {
          id: 3,
          percent: 0,
          job: "",
        },
      ],
    };
  },
  methods: {
    changeParentDataState(id, percent, job) {
      this.containers.map((container) => {
        if (container.id == id) {
          container.percent = percent;
          container.job = job;
          console.log(this.containers);
        }
      });
    },
  },
};
</script>

<template>
  <div class="container">
    <info-block
      v-for="item in containers"
      :key="item.id"
      :percent="item.percent"
      :job="item.job"
      :id="item.id"
      @change-block="changeParentDataState"
    />
  </div>
</template>

<style scoped>
.container {
  width: 1000px;
  padding: 20px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
}
</style>
