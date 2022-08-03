<template>
  <div id="app">
    <NavBar></NavBar>
    <div class="mb-5">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>

import NavBar from './components/Nav-Bar';
export default {
  name: 'App',
  components: {
    'NavBar': NavBar
  }
}
</script>

