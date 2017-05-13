<template>
  <div id="app">
    <div>
      <router-link to="/home">Go to Home!!!</router-link>
      <router-link to="/about">Go to About!!!</router-link>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app2'
}
</script>
