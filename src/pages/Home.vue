<template>
  <div>
    <Header />
    <Carousel />
    <BooksCollection />
  </div>
</template>

<script>
import Header from "../components/Header.vue";
import Carousel from "../components/Carousel.vue";
import BooksCollection from "@/components/BooksCollection.vue";
export default {
  name: "Home",
  components: {
    Header,
    Carousel,
    BooksCollection,
  },
};
</script>

<style></style>
