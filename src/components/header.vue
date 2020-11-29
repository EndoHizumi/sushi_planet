<template>
      <div id="header">
      <h1>Welcome to sushi-planet App</h1>
      <p>{{ message }}</p>
    </div>

</template>

<script>
export default {
    props:{
        message:String
    }
}
</script>

<style>
#header {
  text-align: center;
}
</style>