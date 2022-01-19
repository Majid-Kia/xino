<template>
  <div
    class="card"
    :class="showDetail ? 'active' : ''"
    v-click-outside="closeDetail"
  >
    <div class="card__add" @click="activeDetail">
      <span>+</span>
    </div>
    <div class="card__body">
      <span class="card__body-chip">{{ card.chip.toUpperCase() }}</span>
      <div class="card__body-text">
        <span>{{ card.text.toUpperCase() }}</span>
        <span class="card__body-text--bold">{{ card.value }}</span>
      </div>
    </div>
    <div class="card__detail" v-show="showDetail">
      <h3>CREATE BOOST</h3>
      <div class="seprator">
        <span>Date Period</span>
      </div>
      <div class="card__detail-date">
        <h4>Pick Date Range:</h4>
        <div class="card__detail-date-fields">
          <input type="text" v-model="from" />
          <span>TO</span>
          <input type="text" v-model="until" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    card: {
      type: Object
    }
  },
  directives: {
    clickOutside: {
      bind: function(el, binding, vnode) {
        el.clickOutsideEvent = function(event) {
          if (!(el == event.target || el.contains(event.target))) {
            vnode.context[binding.expression](event);
          }
        };
        document.body.addEventListener("click", el.clickOutsideEvent);
      },
      unbind: function(el) {
        document.body.removeEventListener("click", el.clickOutsideEvent);
      }
    }
  },
  data() {
    return {
      showDetail: false,
      from: "2020/09/10",
      until: "2020/09/10"
    };
  },
  methods: {
    activeDetail() {
      this.showDetail = !this.showDetail;
    },
    closeDetail() {
      this.showDetail = false;
    }
  }
};
</script>

<style lang="scss" scoped>
@import "./card.scss";
</style>
