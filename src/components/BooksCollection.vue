<template>
  <div class="container">
    <h1 class="mt-3">Books</h1>
    <div class="row">
      <div v-for="(value, index) in books" :key="index" class="col-4 gap-3 p-3">
        <div class="card" style="width: 18rem">
          <img
            class="card-img-top"
            :src="value.thumbnail"
            alt="Card image cap"
          />
          <div class="card-body">
            <h5 class="card-title">{{ value.bookName }}</h5>
            <p class="card-text">{{ value.author }}</p>
            <div>
              <p v-if="value.status == 'available'" class="text-success">
                {{ value.status }}
              </p>
              <p v-else class="text-danger">{{ value.status }}</p>
            </div>

            <a href="#" class="btn btn-primary">See detail</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "BooksCollection",
  data() {
    return {
      books: [],
    };
  },
  methods: {
    async getBooks() {
      const { data } = await axios.get("https://localhost:7298/Books");
      console.log(data);
      this.books = [...this.books, ...data];
    },
  },
  mounted() {
    this.getBooks();
  },
};
</script>

<style></style>
