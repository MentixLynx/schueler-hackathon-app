<template>
  <div>
    <h1>Register</h1>
    <input v-model="email" placeholder="Email" />
    <input v-model="password" type="password" placeholder="Password" />
    <button @click="registerUser">Register</button>
    <!-- Emit event to switch to Login -->
    <button @click="$emit('switchToLogin')">Go to Login</button>
    <p>{{ registerMessage }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      registerMessage: ""
    };
  },
  methods: {
    registerUser() {
      if (this.email && this.password) {
        const user = { email: this.email, password: this.password };
        localStorage.setItem("user", JSON.stringify(user));
        this.registerMessage = "User registered successfully!";
        // Emit the register-success event to navigate to Home
        this.$emit("registerSuccess");
      } else {
        this.registerMessage = "Please fill in all fields.";
      }
    }
  }
};
</script>
