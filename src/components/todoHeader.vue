<script setup>
import { RouterLink } from "vue-router";
import TodoView from "../views/TodoView.vue";
</script>

<template>
  <header>
    <nav>
      <div class="branding">
        <img src="../assets/Vue_Logo_Black (1).png" alt="fff" />
        <h1>Vue Todos</h1>
      </div>
      <ul class="nav-router">
        <RouterLink to="/"> Home</RouterLink>
        <RouterLink to="/about"> about</RouterLink>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
header {
  background-color: #f1f1f1;
  nav {
    display: flex;
    align-items: center;
    padding: 25px 16px;

    .branding {
      display: flex;
      align-items: center;
      gap: 8px;
      img {
        max-width: 50px;
      }

      h1 {
        font-size: 24px;
      }
    }

    .nav-router {
      display: flex;
      flex: 1;
      justify-content: flex-end;
      gap: 10px;
      list-style: none;

      a {
        text-decoration: none;
        color: inherit;
      }
    }
  }
}
</style>
