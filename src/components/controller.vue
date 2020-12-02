<template>
  <div id="controller">
    <span id="nowState">state:</span>
    <button id="rotateControll" v-on:click="toggle">{{ state }}</button>
    <p>
      <span>Sushi: {{ count }} yen</span>
      <br />
      <button id="add" v-on:click="addSushi">+</button>
      <button id="reduce" v-on:click="reduceSushi">-</button>
    </p>
  </div>
</template>

<script>
export default {
  props: {
      count: Number,
      state: String,
  },
  methods: {
    addSushi() {
      this.$emit("add_event");
    },
    reduceSushi() {
      if(this.count >0){
        this.$emit("reduce_event");
      }
    },
    toggle() {
      if (this.state == "spin") {
        this.$emit('toggle_state')
      } else {
        this.$emit('toggle_state')
      }
    },
  },
};
</script>

<style>
#controller {
  text-align: center;
}
</style>