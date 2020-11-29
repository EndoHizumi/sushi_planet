<template>
  <div id="app">
    <Header v-bind:message="message"></Header>
    <Controller ref="counter" v-on:add_event="sushi_add" v-on:reduce_event="sushi_reduce"></Controller>
    <Planet v-bind:url=food ref="planet"></Planet>
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
      message: "Twinkle, twinkle, little sushi How I wonder what you are."
    };
  },
  methods: {
    sushi_add: function(){
      this.$refs.planet.add()
    },
    sushi_reduce: function(){
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



</style>
