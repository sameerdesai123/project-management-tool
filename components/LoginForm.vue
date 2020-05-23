<template>
  <v-card 
  elevation="24"
  text-center
  class="justify-center"
  >
    <v-icon v-if="!loginForm" @click="toggleForm">mdi-chevron-double-left</v-icon>
    <v-card-title class="justify-center text-lg-center"><v-icon>mdi-login</v-icon>  {{ pageTask }}</v-card-title>
    <v-card-text>
    <v-form 
      v-if="loginForm"
      ref="form"
      v-model="valid"
      :lazy-validation="lazy"
    >
      <v-text-field
        prepend-icon="mdi-email" 
        name="Username"
        v-model="email"
        :rules="emailRules"
        label="E-mail"
        required
      ></v-text-field>
          
      <v-text-field 
      prepend-icon="mdi-lock" 
      name="Password" 
      v-model="pass"
      :counter="10"
      :rules="passRules"
      label="Password"
      required 
      type="password"></v-text-field>
      <!-- <v-checkbox
        v-model="checkbox"
        :rules="[v => !!v || 'You must agree to continue!']"
        label="Do you agree?"
        required
      ></v-checkbox> -->
    </v-form>
    <RegisterForm v-if="!loginForm" />
    </v-card-text>
    <v-card-actions class="justify-center">
        <v-btn
        :disabled="!valid && loginForm"
        class="primary"
        @click="validate"
      >
        Login
      </v-btn>
      <v-btn
        class="info"
        :hidden="!loginForm"
        @click="toggleForm"
      >
        Register
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>

import RegisterForm from '@/components/RegisterForm.vue'

  export default {
    name: 'LoginForm',
    components: {
      RegisterForm,
    },
    data: () => ({
      pageTask: 'Login',
      valid: true,
      pass: '',
      passRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      lazy: false,
      loginForm: true
    }),

    methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
      toggleForm () {
        this.loginForm = !this.loginForm
        if(this.pageTask === "Login") this.pageTask = "Register"
        else this.pageTask = "Login"
      }
    },
  }
</script>
<style lang="sass" scoped>

</style>