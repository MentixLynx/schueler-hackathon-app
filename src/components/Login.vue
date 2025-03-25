<template>
  <div class="flex flex-col">
    <h1 class="p-4 mx-auto text-3xl font-bold">Login</h1>
    <div>
      <div class="relative text-center">
        <img
          src="https://th.bing.com/th/id/OIP.Bk2aB0IcOYoodghMrFfbjgHaE8?rs=1&pid=ImgDetMain"
          alt="img"
        />
        <div class="absolute top-0 left-0 w-full h-full mt-10 text-center">
          <div class="flex flex-col flex-col-reverse w-full h-full">
            <input
              type="password"
              v-model="password"
              class="m-auto mt-0 rounded-lg input-field"
              placeholder="Password"
            />
            <input
              type="text"
              v-model="email"
              class="m-auto mb-5 rounded-lg mt-44 input-field"
              placeholder="Email"
            />
          </div>
          <div>
            <button class="image-button" @click="loginUser">Click me to log in</button>
          </div>
        </div>
        <p class="mt-5">{{ loginMessage }}</p>
        <!-- Button to switch to Registration -->
        <button class="top-right-button" @click="$emit('switchToRegister')">
          Register miau
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      loginMessage: ""
    };
  },
  methods: {
    loginUser() {
      const storedUser = JSON.parse(localStorage.getItem("user"));
      if (storedUser) {
        if (
          storedUser.email === this.email &&
          storedUser.password === this.password
        ) {
          this.loginMessage = "Login successful!";
          // Emit the login-success event to navigate to Home
          this.$emit("loginSuccess");
        } else {
          this.loginMessage = "Invalid email or password.";
        }
      } else {
        this.loginMessage = "No user found. Please register first.";
      }
    }
  }
};
</script>

<style scoped>
.top-right-button {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 10px 20px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  font-weight: bold;
  cursor: pointer;
}
.image-button {
  width: 200px;
  height: 200px;
  background-image: url("https://i.ebayimg.com/images/g/WCIAAOSwP05izoL5/s-l1600.jpg");
  color: white;
  background-size: cover;
  background-position: center;
  border: none;
  cursor: pointer;
}
.input-field {
  width: 200px;
  height: 30px;
  padding: 5px;
  font-size: 14px;
  text-align: center;
}
</style>
