<template>
  <div id="satellite" v-bind:style="spinObject">
    <div v-for="food in foods" v-bind:key="food.index">
      <span v-bind:class="position_list[food.index]">{{food.item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    speed: Number
  },
  data: function () {
    return {
      count: 0,
      foods: [],
      position_list: ["left_up", "right_up", "left_bottom", "right_bottom"],
      spinObject: {
        "animation-name":  "spin",
        "animation-duration": "1.5s",
        "animation-timing-function": "linear",
        "animation-iteration-count": "infinite",
        "animation-delay": this.speed + "s"
      }
    };
  },
  methods: {
    get_count: function(){
      return this.count
    },
    add: function () {
      this.foods.push({ index: this.count, item: "🍣" });
      this.count++
    },
    reduce: function () {
      if (this.count > 0) {
        this.foods.pop();
        this.count--
      }
    },
  },
};
</script>

<style>
.left_up{
  position: absolute;
  left: 0;
}

.right_up{
  position: absolute;
  right: 0;
}

.left_bottom{
  position: absolute;
  left: 0;
  bottom: 0;
}

.right_bottom{
  position: absolute;
  right: 0;
  bottom: 0;
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