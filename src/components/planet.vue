<template>
      <div id="root">
      <div id="planet">
        <img v-bind:src="url" />
      </div>
      <div id="satellite" class="spin"></div>
    </div>
</template>

<script>
export default {
    props:{
        url:String
    }
}
</script>

<style>
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