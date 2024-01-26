<template>
  <div>
    <Header />
    <div
      class="container d-flex justify-content-center align-items-center"
      style="min-height: 80vh"
    >
      <form class="w-50 border p-5 rounded bg-light" @submit="handleSubmit">
        <h4>Sign In</h4>

        <b-label>Email</b-label>
        <input v-model="form.email" name="email" placeholder="dev@gmail.com" class="form-control" />
        <b-label>Password</b-label>
        <input v-model="form.password" name="password" placeholder="******" class="form-control" />
        <b-alert show variant="danger" v-if="error">{{ errorMsg }}</b-alert>
        <div class="d-flex justify-content-end">
          <button variant="primary" class="mt-2 btn btn-primary" type="submit">Login</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Header from '../components/Header.vue'
export default {
  name: 'Login',
  components: {
    Header
  },
  data() {
    return {
      form: { email: '', password: '' },
      error: false,
      errorMsg: ''
    }
  },
  methods: {
    async handleSubmit(e) {
      e.preventDefault()
      const { data } = await axios.post('https://localhost:7298/User/login', this.form)
      const { status, message } = data
      if (status === 'success') {
        this.$router.push('/dashboard')
      } else {
        this.error = true
        this.errorMsg = message
      }
    },
    async handleOnChange(e) {
      const { name, value } = e.target
      this.form = { ...this.form, [name]: value }
    }
  }
}
</script>

<style></style>
