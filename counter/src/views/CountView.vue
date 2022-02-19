<template>
  <div>
    Clicked: {{ count }} times, count is {{ evenOrOdd }}.
    <hr />
    <button @click="increment">+</button>
    <button @click="decrement">-</button>
    <button @click="incrementIfOdd">Increment if odd</button>
    <button @click="incrementAsync">Increment async</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, computed } from "vue";
import { useStore } from "vuex";

export default defineComponent({
  setup() {
    const store = useStore();

   // mapHalperはcomposition api対応していない模様。
   // なお余談ながらVuturやVuetifyなど、最近触ったものは総じて3系に対応しきれておらず、全般的にVue3への対応自体に時期尚早感を感じる。
    return {
      count: computed(() => store.state.count),
      evenOrOdd: computed(() => store.getters.evenOrOdd),
      increment: () => store.dispatch("increment"),
      decrement: () => store.dispatch("decrement"),
      incrementIfOdd: () => store.dispatch("incrementIfOdd"),
      incrementAsync: () => store.dispatch("incrementAsync"),
    };
  },
});
</script>
