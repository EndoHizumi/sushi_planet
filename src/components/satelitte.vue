<template>
  <div id="satellite" class="spin">
    <div v-for="food in foods" v-bind:key="food.index">
      <span v-bind:class="position_list[food.index]">{{food.item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  components: {
  },
  data: function () {
    return {
      count: 0,
      foods: [],
      position_list: ["left_up", "right_up", "left_bottom", "right_bottom"],
    };
  },
  methods: {
    get_count: function(){
      return this.count
    },
    add: function () {
      var food_num = this.foods.length;
      this.foods.push({ index: food_num, item: "🍣" });
      this.count++
    },
    reduce: function () {
      if (this.foods.length > 0) {
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

.spin {
  animation: spin 1.5s linear infinite;
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