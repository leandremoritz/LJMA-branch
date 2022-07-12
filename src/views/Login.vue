<template>
  <div class="loginPage">
    <form class="box glow" @submit.prevent="login">
      <input type="text" v-model="email" placeholder="email" />
      <input type="text" v-model="password" placeholder="password" />
      <button type="submit">Login</button>
    </form>
    <div v-if="user">Welcome {{ user.full_name }}</div>
  </div>
</template>
<script>
export default {
  computed: {
    user() {
      return this.$store.state.user;
    },
  },
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    login() {
      this.$store.dispatch("login", {
        email: this.email,
        password: this.password,
      });
    },
  },
};
</script>

<style>
.loginPage {
  background-color: rgba(0, 0, 0, 0.205);
  height: 100vh;
}
.box {
  position: relative;
  margin: 10% auto 0;
  width: 50%;
  height: 400px;
  background-color: rgba(0, 0, 0, 0.342);
}
.glow::before,
.glow::after {
  content: "";
  position: absolute;
  left: -2px;
  top: -2px;
  background: linear-gradient(45deg, crimson, blue, crimson, blue);
  background-size: 400%;
  width: calc(100% + 5px);
  height: calc(100% + 5px);
  z-index: -5;
  animation: animate 20s linear infinite;
}
@keyframes animate {
  0% {
    background-position: 0 0;
  }
  50% {
    background-position: 400% 0;
  }
  100% {
    background-position: 0 0;
  }
}
.glow::after {
  filter: blur(80px);
}
</style>
