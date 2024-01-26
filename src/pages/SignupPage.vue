<template>
  <div>
    <Header />
    <div
      class="container d-flex justify-content-center align-items-center"
      style="min-height: 80vh"
    >
      <b-form class="w-50 border p-5 rounded bg-light" @submit="handleSignup">
        <h4>Signup</h4>

        <b-label>First Name</b-label>
        <input
          class="form-control"
          v-model="formData.fName"
          name="fName"
          placeholder="Sam"
          @change="handleChange"
        />
        <b-label>Last Name</b-label>
        <input
          v-model="formData.lName"
          name="lName"
          placeholder="Kurt"
          @change="handleChange"
          class="form-control"
        />
        <b-label>Email</b-label>
        <input
          v-model="formData.email"
          name="email"
          placeholder="dev@gmail.com"
          @change="handleChange"
          class="form-control"
        />
        <b-label>Password</b-label>
        <input
          v-model="formData.password"
          name="password"
          placeholder="******"
          @change="handleChange"
          class="form-control"
        />
        <b-label>Confirm Password</b-label>
        <input
          v-model="formData.confirmPass"
          name="confirmPass"
          placeholder="******"
          @change="handleChange"
          class="form-control"
        />
        <div class="d-flex justify-content-end">
          <b-button variant="primary" type="submit" class="mt-2 btn btn-primary">Register</b-button>
        </div>
      </b-form>
    </div>
  </div>
</template>

<script>
import Header from '../components/Header.vue'
import axios from 'axios'
// import VueAxios from "vue-axios";
export default {
  name: 'Signup',
  components: {
    Header
  },
  data() {
    return {
      formData: {
        fName: '',
        lName: '',
        email: '',
        password: '',
        confirmPass: ''
      }
    }
  },
  methods: {
    handleChange() {
      console.log(this.formData)
    },
    async handleSignup(e) {
      e.preventDefault()
      const { confirmPass, ...rest } = this.formData
      if (confirmPass !== rest.password) {
        return
      }
      const { data } = await axios.post(' https://localhost:7298/User', rest)
      const { status } = data
      if (status === 'success') this.$router.push('/login')
      return
    }
  }
}
</script>

<style></style>
