
<template>
<!--
  <nav class="navbar navbar-expand-md navbar-dark bg-dark mb-4">
    <div class="container-fluid">
      <router-link to="/" class="navbar-brand">Home</router-link>

      <div>
        <ul class="navbar-nav me-auto mb-2 mb-md-0" v-if="!auth">
          
          <li class="nav-item">
            <router-link to="/" class="nav-link">Login</router-link>
          </li>

        </ul>

        <ul class="navbar-nav me-auto mb-2 mb-md-0" v-if="auth">
          <li class="nav-item">
            <a href="#" class="nav-link" @click="logout">Logout</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  -->
  <div>
    <Mensaje msg="Sisparking" />
  </div>
</template>

<script lang="ts">
import { computed } from "vue";
import { useStore } from "vuex";
import Mensaje from "./HomeView.vue";
export default {
  components: {
    Mensaje,
  },
  name: "Nav",
  setup() {
    const store = useStore();
    const auth = computed(() => store.state.authenticated);
    const logout = async () => {
      await fetch("http://localhost:8000/api/logout", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        credentials: "include",
      });
    };
    return {
      auth,
      logout,
    };
  },
};
</script>