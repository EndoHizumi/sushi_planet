<template>
  <div id="root">
    <div id="planet">
      <img v-bind:class="state" v-bind:src="url" />
    </div>
    <Satelitte
      v-for="data of satellite_data"
      v-bind:key="data.index"
      v-bind:ref="'satelitte'"
      v-bind:speed="data.spinSpeed"
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
      speed: 1.5,
      satellite_data: [{ index: 1, spinSpeed: 1.5 }],
    };
  },
  methods: {
    add: function () {
      let satellite_num = this.satellite_data.length;
      let current_satelitte = this.$refs["satelitte"][satellite_num - 1];
      current_satelitte.add();
      if (current_satelitte.get_count() > 3) {
        this.satellite_data.push({
          index: satellite_num + 1,
          spinSpeed: (this.speed + (satellite_num * 0.2)),
        });
      }
    },
    reduce: function () {
      let satellite_num = this.satellite_data.length - 1;
      let current_satelitte = this.$refs["satelitte"][satellite_num - 1];
      if (current_satelitte.get_count() <= 0 && satellite_num > 0) {
        this.satellite_data.pop();
        current_satelitte = this.$refs["satelitte"][satellite_num - 1];
      }
      if (current_satelitte.get_count() > 0) {
        current_satelitte.reduce();
      }
    },
  },
};
</script>

<style>
.rotation {
  animation: spin 50s linear infinite;
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