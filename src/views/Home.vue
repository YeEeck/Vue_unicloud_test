<template>
  <div class="home">
    <div id="navin">
      <router-link to="/home/login">Login</router-link> |
      <router-link to="/home/reg">Reg</router-link>
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  name: "Home",
};
</script>

<style>
#nav {
  padding: 10px;
}

#navin a {
  font-weight: bold;
  color: #2c3e50;
}

#navin a.router-link-exact-active {
  color: #42b983;
}
</style>