<template>
  <div id="root">
    <div id="planet">
      <img v-bind:class="state" v-bind:src="url" />
    </div>
    <Satelitte
      v-for="num of satellite_nums"
      v-bind:key="num"
      v-bind:ref="'satelitte'"
    ></Satelitte>
  </div>
</template>

<script>
import Satelitte from "./satelitte";
export default {
  components: { Satelitte },
  props: {
    url: String,
    state: String,
  },
  data: function () {
    return {
      satellite_nums: 1,
    };
  },
  methods: {
    add: function () {
      let current_satelitte = this.$refs['satelitte'][this.satellite_nums -1]
      if (current_satelitte.get_count() > 2) {
        this.satellite_nums++
      }
      current_satelitte.add();
    },
    reduce: function () {
      let current_satelitte = this.$refs['satelitte'][this.satellite_nums -1]
      if (current_satelitte.get_count() > 0) {
        this.satellite_nums--
        current_satelitte = this.$refs['satelitte'][this.satellite_nums -1]
      }
      current_satelitte.reduce();
    },
  },
};
</script>

<style>
.rotation {
  animation: spin 15s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>