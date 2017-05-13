<template>
  <div class="home">
    <h1>Home</h1><p>{{message}}</p>
  </div>
</template>

<script>
export default {
  name: 'home',
  data () {
    return {
      message: 'Hello,Vue router!'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
