<template>
    <v-container>
      <v-row justify="center">
        <v-col cols="12" sm="8" lg="6">
          <v-card class="elevation-12">
            <v-toolbar dark color="primary" class="pl-4">
              <v-toolbar-title>Registration</v-toolbar-title>
            </v-toolbar>
  
            <v-card-text>
              <v-form v-model="valid" ref="form" lazy-validation>
                <v-text-field
                  prepend-icon="mdi-account"
                  name="email"
                  label="Email"
                  type="email"
                  v-model="email"
                  :rules="emailRules"
                ></v-text-field>
  
                <v-text-field
                  prepend-icon="mdi-lock"
                  name="password"
                  label="Password"
                  type="password"
                  v-model="password"
                  :rules="passwordRules"
                ></v-text-field>
  
                <!-- Новый блок для подтверждения пароля -->
                <v-text-field
                  prepend-icon="mdi-lock"
                  name="confirm-password"
                  label="Confirm Password"
                  type="password"
                  v-model="confirmPassword"
                  :rules="confirmPasswordRules"
                ></v-text-field>
              </v-form>
            </v-card-text>
  
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn
                color="primary"
                @click="onSubmit"
                :disabled="!valid"
              >
                Create Account
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        email: "",
        password: "",
        confirmPassword: "", // Добавляем переменную для подтверждения пароля
        valid: false,
        emailRules: [
          v => !!v || "E-mail is required",
          v => /.+@.+\..+/.test(v) || "E-mail must be valid"
        ],
        passwordRules: [
          v => !!v || "Password is required",
          v => (v && v.length >= 6) || "Password must be at least 6 characters"
        ],
        confirmPasswordRules: [
          v => !!v || "Confirm Password is required", // Обязательно для заполнения
          v => v === this.password || "Password should match" // Проверка на совпадение
        ]
      };
    },
    methods: {
      onSubmit() {
        if (this.$refs.form.validate()) {
          const newUser = {
            email: this.email,
            password: this.password
          };
          console.log("🟢 Зарегистрирован пользователь:", newUser);
          // Здесь можно добавить логику для отправки данных или перехода на другую страницу
        }
      }
    }
  };
  </script>
  