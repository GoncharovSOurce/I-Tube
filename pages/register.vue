<template>
  <b-container class="d-flex justify-content-center">
    <b-form @submit.prevent="onSubmit" class="auth-form">
      <h2 class="text-center">
        Регистрация
      </h2>
      <hr>

      <b-form-group
        label ="Login:"
        label-for ="name"
      >
        <b-form-input
          id="name"
          v-model="form.name"
          type="text"
          required
          placeholder="Login..."
        />
      </b-form-group>
      <b-form-group
        label ="Email:"
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


      <b-button class="btn-block" type="submit" pill variant="primary">
        Зарегистрироваться
      </b-button>
      <nuxt-link :to="{ name: 'login' }" class="btn btn-link btn-block" tag="button">
        Авторизоваться
      </nuxt-link>

    </b-form>
  </b-container>
</template>

<script>
  export default {
    name: "Register",
    auth: false,
    middleware: ['login'],
    layout: 'empty',
    data: () => ({
        form: {
          firstName: '',
          lastName: '',
          email: '',
          password:''
          }
     }),
      methods: {
        async onSubmit () {
          try {
            await this.$axios.$post('/register', this.form),
            await this.$auth.loginWith('local',{
              data: {
                email: this.form.email ,
                password: this.form.password
              }
            })
          } catch (e) {
            console.log(e.response);
          }
        }
      }
    }
</script>

<style scoped>

</style>
