<template>
  <div class="sidenav">
    <ul class="nav-items">
      <li class="nav-logo">
        <router-link class="logo-link" to="/">
          <img class="logo" src="../../assets/logo.png" alt="TechyDM" />
        </router-link>
      </li>
      <li v-for="tool in tools" :key="tool.name" class="nav-item">
        <router-link :to="tool.path" class="nav-link">
          <i :class="tool.icon" /> <span class="nav-text">{{ tool.name }}</span>
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import ToolServices from "@/services/tools";
export default {
  name: "NavBar",
  setup() {
    return { ...ToolServices() };
  }
};
</script>

<style scoped lang="scss">
@import "../../assets/styles";

.sidenav {
  background-color: $primary;
  transition: width 250ms ease;
}

.nav-items {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
}

.nav-item {
  width: 100%;
}

.nav-item:last-child {
  margin-top: auto;
}

.nav-link {
  display: flex;
  align-items: center;
  height: 5rem;
  color: $light;
}

.nav-link:hover {
  color: $accent;
  background-color: $dark;
}

.nav-link i {
  min-width: 2rem;
  margin: 0 0.5rem;
}

.nav-logo {
  font-weight: bold;
  text-transform: uppercase;
  margin-bottom: 1rem;
  text-align: center;
  color: $light;
  background-color: $dark;
  font-size: 1.5rem;
  letter-spacing: 0.3ch;
  width: 100%;
}

.logo-link {
  height: 100%;
  width: 100%;
}

.logo {
  max-width: 5rem;
}

.nav-text {
  display: none;
  margin-left: 1rem;
  color: $light;
}

@media only screen and (max-width: 600px) {
  .sidenav {
    width: 100vw;
    height: 5rem;
  }

  .nav-logo {
    display: none;
  }

  .nav-items {
    flex-direction: row;
  }

  .nav-link {
    justify-content: center;
  }
}

@media only screen and (min-width: 600px) {
  .sidenav {
    width: 5rem;
    height: 100vh;
  }

  .sidenav:hover {
    width: 16rem;
  }

  .sidenav:hover .nav-text {
    display: inline;
    transition: opacity 250ms ease;
  }
}
</style>
