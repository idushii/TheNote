<template>
  <div id="app" 
    @mousemove="processMove" 
    @click="e => $store.dispatch('hideContext', { e })"
    @click.right.prevent="e => $store.dispatch('showContex', {Top: e.y, Left: e.x, Show: true, Type: 'List', e})"
  >
    <router-view></router-view>
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "app",
  data() {
    return {
    };
  },
  computed: {
      ...mapGetters(["isMoveNote", "isMovePanel"]),
  },
  methods: {
    processMove(e) {
      if (this.isMoveNote)    this.$store.commit("processMove", { Top: e.y, Left: e.x });
      if (this.isMovePanel)   this.$store.commit("processMovePanel", { Top: e.y, Left: e.x });
    },
  },
  mounted() {
  }
};
</script>

<style lang="scss">
html,
body,
#app {
  width: 100%;
  height: 100%;
}
</style>
