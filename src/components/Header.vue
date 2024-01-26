<template>
  <div class="header-container text-light">
    <div class="d-flex justify-content-around align-items-center h-100">
      <router-link to="/" class="nav-link"><h3>Library</h3></router-link>
      <div class="d-flex gap-3">
        <router-link to="/dashboard" class="nav-link">Dashboard</router-link>
        <router-link to="/login" class="nav-link"> Login</router-link>
        <router-link to="/signup" class="nav-link"> Signup</router-link>
        <span> Books</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style>
.header-container {
  height: 10vh;
  background-color: rgb(39, 39, 39);
}
</style>
