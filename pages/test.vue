<template>
  <div>
    <form @submit.prevent="userLogin">
      <div>
        <label>Username</label>
        
        <v-text-field
            v-model="login.username"
            label="Outlined"
            placeholder="Placeholder"
            outlined
          />
      </div>
      <div>
        <label>Password</label>
        
        <v-text-field
            v-model="login.password"
            label="Outlined"
            placeholder="Placeholder"
            outlined
          />
      </div>
      <div>
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      login: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('local', { data: this.login })
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>