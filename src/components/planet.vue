<template>
      <div id="root">
      <div id="planet">
      <img v-bind:class="state" v-bind:src="url" />
    </div>
</template>

<script>
export default {
  props: {
    url: String,
    state: String,
  },
    methods:{
        add:function(){
            console.log('planet add')
        },
        reduce: function(){
            console.log('planet_reduce')
        }
    }
}
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