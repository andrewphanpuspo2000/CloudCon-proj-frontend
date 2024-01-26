<template>
  <div>
    <DashboardNav />
    <AddBookModal :dataBooks="books" />
    <div class="w-100 d-flex">
      <Sidebar />
      <div class="p-5 bg-light" style="width: 80%">
        <div class="d-flex justify-content-between mb-3">
          <h3>Add Book</h3>
          <button
            type="button"
            class="btn btn-primary"
            data-bs-toggle="modal"
            data-bs-target="#exampleModal"
          >
            Add Book
          </button>
        </div>
        <table border="1" class="w-100">
          <tr>
            <th>Status</th>
            <th>Name</th>
            <th>Thumbnail</th>
            <th>Author</th>
            <th>Published</th>
          </tr>
          <tr v-for="(value, index) in books" :key="index">
            <td>{{ value.status }}</td>
            <td>{{ value.bookName }}</td>
            <td>
              <img :src="value.thumbnail" style="width: 70px; height: 70px" />
            </td>
            <td>{{ value.author }}</td>
            <td>{{ value.published }}</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import AddBookModal from "../components/AddBookModal.vue";
import DashboardNav from "../components/DashboardNav.vue";
import Sidebar from "../components/Sidebar.vue";

export default {
  name: "Dashboard",
  data() {
    return {
      optionsSide: ["Add Book", "Borrow"],
      books: [],
    };
  },
  methods: {
    async getBooks() {
      const { data } = await axios.get("https://localhost:7298/Books");
      this.books = [...this.books, ...data];
    },
  },
  mounted() {
    this.getBooks();
  },
  components: {
    DashboardNav,
    Sidebar,
    AddBookModal,
  },
};
</script>

<style>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td,
th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>
