<template>
  <b-container class="d-flex justify-content-center">
    <b-form class="auth-form">
      <b-form-group
          label ="Email address:"
          label-for ="email"
          >
          <b-form-input
            id="email"
            v-model="form.email"
            type="email"
            required
            placeholder="Enter email..."
          />
      </b-form-group>
      <b-form-group
        label ="Password:"
        label-for ="password"
      >
        <b-form-input
          id="password"
          v-model="form.password"
          type="password"
          required
          placeholder="Enter password..."
        />
      </b-form-group>
    </b-form>
  </b-container>
</template>

<script>
    export default {
        name: "Login",
        auth: false,
        data: () => ({
            form: {
              email: ''
            }
        })
    }
</script>

<style scoped="scss">
  .auth-form {
    width: 450px;
    padding-top: 200px;
  }

</style>
