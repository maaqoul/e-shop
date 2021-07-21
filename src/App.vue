<template>
  <div >
    <nav>
      <div class="container">
        <ul class="nav__left">
          <li v-for="route of routes" :key="route.path">
            <router-link :to="route.path">{{route.name}}</router-link></li>
        </ul>
      </div>
    </nav>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      routes: [
        {
          path: '/',
          name: 'Home',
        },
        {
          path: '/admin',
          name: 'Admin',
        },
        {
          path: '/cart',
          name: 'Cart',
        },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
