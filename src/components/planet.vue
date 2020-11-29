<template>
      <div id="root">
      <div id="planet">
        <img v-bind:src="url" />
      </div>
    </div>
</template>

<script>
export default {
    props:{
        url:String
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