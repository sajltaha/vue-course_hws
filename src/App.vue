<script>
export default {
  data: () => {
    return {
      cardOne: {
        cardOneTitle: "Title 1",
        cardOneDesc: "Description 1",
        cardOnePrice: "$0",
        cardOneSrc: "wrong_src",
        cardOneId: 12321,
      },
      cardTwo: {
        cardTwoDesc: "Description 2",
        cardTwoTitle: "Title 2",
        cardTwoPrice: "$0",
        cardTwoSrc: "wrong_src",
        cardTwoId: 32123,
      },
      cardList: [1, 2],
      selected: 0,
      title: "",
      description: "",
      price: "",
      id: "",
      src: "",
    };
  },
  methods: {
    changeCard() {
      if (this.selected == 1) {
        this.cardOne.cardOneTitle = this.title;
        this.cardOne.cardOneDesc = this.description;
        this.cardOne.cardOneId = this.id;
        this.cardOne.cardOnePrice = this.price;
        this.cardOne.cardOneSrc = this.src;
        this.clear();
      } else {
        this.cardTwo.cardTwoTitle = this.title;
        this.cardTwo.cardTwoDesc = this.description;
        this.cardTwo.cardTwoId = this.id;
        this.cardTwo.cardTwoPrice = this.price;
        this.cardTwo.cardTwoSrc = this.src;
        this.clear();
      }
    },
    clear() {
      this.title = "";
      this.src = "";
      this.description = "";
      this.id = "";
      this.price = "";
      this.selected = 0;
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="card">
      <p>ID:{{ cardOne.cardOneId }}</p>
      <img class="img" :src="cardOne.cardOneSrc" alt="wrong link" />
      <h1>{{ cardOne.cardOneTitle }}</h1>
      <p>{{ cardOne.cardOneDesc }}</p>
      <h3>{{ cardOne.cardOnePrice }}</h3>
    </div>
    <div class="card">
      <p>ID:{{ cardTwo.cardTwoId }}</p>
      <img class="img" :src="cardTwo.cardTwoSrc" alt="wrong link" />
      <h1>{{ cardTwo.cardTwoTitle }}</h1>
      <p>{{ cardTwo.cardTwoDesc }}</p>
      <h3>{{ cardTwo.cardTwoPrice }}</h3>
    </div>
  </div>
  <form class="form">
    <input type="text" placeholder="Title" v-model="title" />
    <input type="text" placeholder="Description" v-model="description" />
    <input type="text" placeholder="Source" v-model="src" />
    <input type="number" placeholder="ID" v-model="id" />
    <input type="number" placeholder="Price" v-model="price" />
    <p>Select card:</p>
    <select v-model="selected">
      <option v-for="(card, key) in cardList" :key="key" :value="card">
        {{ card }}
      </option>
    </select>
    <button
      type="button"
      :disabled="
        !title || !description || !src || !id || !price || selected == 0
      "
      @click="changeCard"
    >
      Change
    </button>
  </form>
</template>

<style scoped>
.card {
  width: 200px;
  height: 300px;
  background-color: wheat;
  border-radius: 15px;
  border: 3px solid brown;
  display: flex;
  text-align: center;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  color: black;
}
.container {
  display: flex;
  width: 500px;
  margin: 0 auto;
  gap: 20px;
  padding-top: 30px;
  padding-bottom: 20px;
  justify-content: center;
}

.form {
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  width: 500px;
  align-items: center;
  gap: 10px;
  padding: 10px;
}

.img {
  width: 100px;
  height: 100px;
}
</style>
