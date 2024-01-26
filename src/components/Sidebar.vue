<template>
  <div class="sidebar bg-dark p-3">
    <ul style="list-style: none">
      <li class="text-light mt-5" v-for="(item, index) in optionsSide" :key="index">
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'sidebar',
  data() {
    return {
      optionsSide: ['Add book', 'Borrow']
    }
  }
}
</script>

<style>
.sidebar {
  min-height: 100vh;
  width: 20%;
}
</style>
