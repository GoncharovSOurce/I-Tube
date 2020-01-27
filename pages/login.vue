<template>
  <div>
  <b-container class="d-flex justify-content-center">
    <b-form @submit.prevent="onSubmit" class="auth-form">
      <h2 class="text-center">
        Авторизоваться
      </h2>
      <hr>
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
        Войти
      </b-button>
      <b-button class="btn-block" pill variant="secondary" >
        Забыл пароль?
      </b-button>
      <nuxt-link :to="{ name: 'register' }" class="btn btn-link btn-block" tag="button">
        Зарегистрироваться
      </nuxt-link>


    </b-form>
  </b-container>
  </div>
</template>

<script>


    import TheHeader from "../components/TheHeader";
    export default {
      name: 'Login',
      components: { TheHeader, },
      layout: 'empty' ,
      data: () => ({
            form: {
              email: '',
              password:''
            }
      }),
      methods: {
        async onSubmit() {
          await this.$auth.loginWith('local', { data: this.form } )
        }
      }
    }
</script>

<style scoped>

</style>

