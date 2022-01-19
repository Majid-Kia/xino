<template>
  <div id="app">
    <AddCard :createCard="addCard" />
    <div class="container">
      <Cards :cards="cards" />
    </div>
  </div>
</template>

<script>
import AddCard from "./components/addCard/AddCard";
import Cards from "./components/cards/Cards";
export default {
  name: "App",
  components: {
    AddCard,
    Cards
  },
  data() {
    return {
      cards: [
        {
          id: new Date().toISOString(),
          chip: "boost",
          text: "liking",
          value: 100
        }
      ]
    };
  },
  methods: {
    addCard() {
      // must use uuid for unique id generator but in the task requirements said don't use external packages
      const newCardData = {
        id: new Date().toISOString(),
        chip: "boost",
        text: "liking",
        value: 100
      };
      this.cards.push(newCardData);
    }
  }
};
</script>

<style lang="scss">
@import "@/scss/global.scss";
#app {
  padding: 40px;
}
</style>
