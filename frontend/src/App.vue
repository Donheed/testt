<template>
  <div id="app">
    <Navbar v-if="isLoggedIn" @logout="handleLogout" />
    <div v-if="!isLoggedIn">
      <LoginForm @login-success="handleLoginSuccess" />
    </div>
    <div v-else>
      <h1>Welcome to Homepage</h1>
      <p>Selamat meminjam barang.</p>
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from 'vue';
import LoginForm from './components/LoginForm.vue';
import Navbar from './components/Navbar.vue';

export default {
  components: {
    LoginForm,
    Navbar,
  },
  setup() {
    const isLoggedIn = ref(!!localStorage.getItem('token'));

    const handleLoginSuccess = () => {
      isLoggedIn.value = true;
    };

    const handleLogout = () => {
      isLoggedIn.value = false; // Ubah status login menjadi false
    };

    return { isLoggedIn, handleLoginSuccess, handleLogout };
  },
};
</script>

<style>
/* Tambahkan gaya sesuai kebutuhan */
</style>
