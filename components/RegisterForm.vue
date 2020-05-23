<template>
  <v-form
      ref="form"
      v-model="valid"
      :lazy-validation="lazy"
    >
      <v-text-field prepend-icon="mdi-account" name="User" label="Username"></v-text-field>
      <v-text-field
        prepend-icon="mdi-email" 
        name="Email"
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

      <v-text-field 
      prepend-icon="mdi-lock" 
      name="CNF_Password" 
      v-model="pass"
      :counter="10"
      :rules="passRules"
      label="Confirm Password"
      required 
      type="password"></v-text-field>
    </v-form>
</template>

<script>
export default {
  data: () => ({
      pageTask: 'Login',
      valid: true,
      pass: '',
      passRules: [
        v => !!v || 'Password is required',
        v => (v && v.length <= 10 && v.length >= 6) || 'Name must be between 6 to 10 characters',
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
      }
    },
}
</script>