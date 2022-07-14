<template>
  <div class="hello">
    <form @submit.prevent="signUp">
      <input type="text" v-model="full_name" placeholder="Fullname" />
      <input type="text" v-model="email" placeholder="email" />
      <input type="text" v-model="password" placeholder="password" />
      <button type="submit">Sign Up</button>
    </form>
    <div v-if="user">Welcome {{ user.full_name }}</div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      user: null,
      full_name: "",
    };
  },
  methods: {
    signUp() {
      fetch("http://localhost:3000/users", {
        method: "POST",
        body: JSON.stringify({
          full_name: this.full_name,
          email: this.email,
          password: this.password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => console.log(json));
    },
  },
};
</script>
