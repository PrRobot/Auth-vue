<template>
  <div class="navbar__container">
    <div class="navbar">
      <div class="navbar__left">
        <router-link class="router__link" to="/">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="logo"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              d="M10.394 2.08a1 1 0 00-.788 0l-7 3a1 1 0 000 1.84L5.25 8.051a.999.999 0 01.356-.257l4-1.714a1 1 0 11.788 1.838L7.667 9.088l1.94.831a1 1 0 00.787 0l7-3a1 1 0 000-1.838l-7-3zM3.31 9.397L5 10.12v4.102a8.969 8.969 0 00-1.05-.174 1 1 0 01-.89-.89 11.115 11.115 0 01.25-3.762zM9.3 16.573A9.026 9.026 0 007 14.935v-3.957l1.818.78a3 3 0 002.364 0l5.508-2.361a11.026 11.026 0 01.25 3.762 1 1 0 01-.89.89 8.968 8.968 0 00-5.35 2.524 1 1 0 01-1.4 0zM6 18a1 1 0 001-1v-2.065a8.935 8.935 0 00-2-.712V17a1 1 0 001 1z"
            /></svg
        ></router-link>
      </div>
      <div class="navbar__right">
        <div v-if="!user">
          <router-link class="router__link" to="/login"
            ><h5>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                stroke-width="2"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M11 16l-4-4m0 0l4-4m-4 4h14m-5 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h7a3 3 0 013 3v1"
                /></svg
              >Login
            </h5></router-link
          >
        </div>
        <a v-if="user" class="router__link" href="" @click.prevent="logout"
          ><svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1"
            /></svg
          >Logout</a
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: "",
    };
  },
  mounted() {
    if (localStorage.activeUser) {
      let activeUser = localStorage.activeUser;
      this.user = JSON.parse(activeUser);
    }
  },
  methods: {
    logout() {
      localStorage.removeItem("activeUser");
      this.$router.push("/login");
      window.location.reload();
    },
  },
};
</script>

<style>
.navbar__container {
  position: fixed;
  top: 12px;
  width: 100%;
  display: flex;
  justify-content: center;
  z-index: 1;
}
.navbar {
  width: 98%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 8px 50px;

  box-shadow: 0 6px 8px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  border-radius: 10px;
}
.navbar__left h1 {
  margin: 0;
  cursor: pointer;
  color: rgb(255, 255, 255);
}
.navbar__right > h3 {
  cursor: pointer;
  color: rgb(255, 255, 255);
}
.router__link {
  text-decoration: none;
  color: rgb(225, 225, 225);
  display: flex;
  align-items: center;
}
.router__link:hover {
  text-decoration: none;
  color: rgb(115, 227, 247);
}
.logo {
  width: 30px;
}
svg {
  width: 18px;
  padding-top: 2px;
}
</style>
