<template>
  <div id="app">
    <Header v-bind:message="message"></Header>
    <Controller v-bind:state=state v-bind:count=count v-on:add_event="sushi_add" v-on:reduce_event="sushi_reduce" v-on:toggle_state="rotate_toggle"></Controller>
    <Planet v-bind:url=food v-bind:state=state ref="planet"></Planet>
  </div>
</template>

<script>
import Header from "./components/header.vue"
import Controller from "./components/controller.vue"
import Planet from "./components/planet.vue"
import ChawanmushiImage from "@/assets/Chawan-Mushi.png";

export default {
  name: "App",
  components: {
    Header,
    Controller,
    Planet
  },
  data: function () {
    return {
      food: ChawanmushiImage,
      message: "Twinkle, twinkle, little sushi How I wonder what you are.",
      count: 0
    };
  },
  methods: {
    rotate_toggle: function(){
      if (this.state == "rotation") {
        this.state = "stop";
      } else {
        this.state = "rotation";
      }
    },
    sushi_add: function(){
      this.count++ 
      this.$refs.planet.add()
    },
    sushi_reduce: function(){
      this.count-- 
      this.$refs.planet.reduce()
    }
  }
};
</script>

<style>
body {
  background-image: url("./assets/maeda3gou1929007_TP_V.jpg");
  color: whitesmoke;
}
#root {
  display: flex;
  justify-content: center;
  margin: 50px;
}
#planet {
  background-color: transparent;
  height: 100%;
  text-align: center;
}
#satellite {
  position: absolute;
  width: 250px;
  height: 250px;
  text-align: center;
}
.stop {
  filter: grayscale(100%);
}

</style>
