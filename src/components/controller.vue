<template>
  <div id="controller">
    <span id="nowState">state:</span>
    <button id="rotateControll" v-on:click="toggle">{{ state }}</button>
    <p>
      <span>Sushi:{{ count }} yen</span>
      <br />
      <button id="add" v-on:click="addSushi">+</button>
      <button id="reduce" v-on:click="reduceSushi">-</button>
    </p>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      count: 0,
      state: "spin",
    };
  },
  methods:{
    addSushi(){
     this.$emit('add_event') 
    },
    reduceSushi(){
      this.$emit('reduce_event')
    }
  }
};
</script>

<style>
#controller {
  text-align: center;
}
</style>