<template>
  <button @click="createCard">Add Card</button>
</template>

<script>
export default {
  name: "AddCard",
  props: ["createCard"]
};
</script>

<style scoped lang="scss">
@import "./addCard.scss";
</style>
