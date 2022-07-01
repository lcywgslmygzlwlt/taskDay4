<template>
  <div>
    {{msg}}
    {{msg | toUp}}
    {{msg | toReverse}}
  </div>
</template>

<script>
export default {
  data(){
    return{
      msg:'hello,vue'
    }
  },
  filters:{
    toUp(val){
      return val.toUpperCase()
    },
  }
}
</script>

<style>

</style>