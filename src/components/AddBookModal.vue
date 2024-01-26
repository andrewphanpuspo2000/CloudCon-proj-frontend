<template>
  <div
    class="modal fade"
    id="exampleModal"
    tabindex="-1"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h1 class="modal-title fs-5" id="exampleModalLabel">Add Book</h1>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <label>Book Name</label>
          <input
            v-model="name"
            placeholder="Enter book name"
            class="form-control"
          />
          <label>Author</label>
          <input
            v-model="author"
            placeholder="Author Name"
            class="form-control"
          />
          <label>Published Date</label>
          <input
            v-model="published"
            placeholder="Published Date"
            type="date"
            class="form-control"
          />
          <label>Thumbnail</label>
          <input
            v-model="thumbnail"
            placeholder="Thumbnail"
            class="form-control"
          />
        </div>
        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
          >
            Close
          </button>
          <button
            type="button"
            @click="handleAddBook"
            class="btn btn-primary"
            data-bs-dismiss="modal"
          >
            Add
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "AddBookModal",
  props: ["dataBooks"],
  data() {
    return {
      name: "",
      author: "",
      published: null,
      thumbnail: "",
    };
  },
  methods: {
    async handleAddBook() {
      if (
        this.name.length === 0 ||
        this.author.length === 0 ||
        this.published === null ||
        this.thumbnail.length === 0
      ) {
        return;
      } else {
        const { data } = await axios.post("https://localhost:7298/Books", {
          bookName: this.name,
          author: this.author,
          published: this.published,
          thumbnail: this.thumbnail,
        });
        if (data.status === "success") {
          console.log(this.dataBooks);
          this.dataBooks = [
            ...this.dataBooks,
            {
              bookName: this.name,
              author: this.author,
              published: this.published,
              thumbnail: this.thumbnail,
            },
          ];
          this.name = "";
          this.author = "";
          this.published = "";
          this.thumbnail = "";
        }
      }
    },
  },
};
</script>

<style></style>
