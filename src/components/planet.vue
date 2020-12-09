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
      satellite_data: [{ index: 1, spinSpeed: 0 }],
    };
  },
  computed:{
    satellite_num: function(){
      return this.satellite_data.length
    },
    current_satelitte: function(){
      return this.$refs["satelitte"][this.satellite_num - 1];
    }
  },
  methods: {
    add: function () {
      this.current_satelitte.add();
      if (this.current_satelitte.get_count() > 3) {
        this.satellite_data.push({
          index: this.satellite_num + 1,
          spinSpeed: this.satellite_num * 0.2,
        });
      }
    },
    reduce: function () {
      if (this.current_satelitte.get_count() <= 0 && this.satellite_num > 0) {
        this.satellite_data.pop();
      }
      if (this.current_satelitte.get_count() > 0) {
        this.current_satelitte.reduce();
      }
    },
    die: function(){
      this.satellite_data.length = 0
    },
    reborn: function(){
      this.satellite_data.push({
          index: 1,
          spinSpeed: 0,
        });
    }
  },
};
</script>

<style>
.rotation {
  animation: spin 50s linear infinite;
}

.die {
  filter: grayscale(100%);
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