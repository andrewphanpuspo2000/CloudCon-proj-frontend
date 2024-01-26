<template>
  <div>
    <b-carousel
      id="carousel-1"
      v-model="slide"
      :interval="4000"
      controls
      indicators
      background="#ababab"
      style="text-shadow: 1px 1px 2px #333; height: 60vh; overflow: hidden"
    >
      <b-carousel-slide
        :img-src="libPhoto"
        style="height: 60vh; overflow: hidden"
      ></b-carousel-slide>
      <b-carousel-slide
        :img-src="libPhoto"
        style="height: 60vh; overflow: hidden"
      ></b-carousel-slide>
      <b-carousel-slide
        :img-src="libPhoto"
        style="height: 60vh; overflow: hidden"
      ></b-carousel-slide>
    </b-carousel>
  </div>
</template>

<script>
// import libPhoto from '../assets/library-img.jpg'
export default {
  name: "Carousel",
  data() {
    return {
      slide: 0,
      sliding: null,
      // libPhoto
    };
  },
};
</script>

<style>
img {
  object-fit: cover;
}
</style>
