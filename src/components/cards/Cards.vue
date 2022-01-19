<template>
  <div class="cards-wrapper">
    <div v-for="card in cards" :key="card.id">
      <Card :card="card" />
    </div>
  </div>
</template>

<script>
import Card from "@/components/card/Card";
export default {
  components: {
    Card
  },
  props: {
    cards: {
      type: Array
    }
  }
};
</script>

<style lang="scss" scoped>
@import "./cards.scss";
</style>
