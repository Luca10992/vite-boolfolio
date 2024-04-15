<script></script>

<template>
  <div class="container">
    <div class="nav-bar d-flex justify-content-between align-items-center">
      <div class="nav-link d-flex gap-4">
        <div class="logo">
          <router-link :to="{ name: 'home' }">
            <strong>Boolfolio</strong>
          </router-link>
        </div>
        <div class="link-box d-flex gap-3">
          <router-link :to="{ name: 'project' }">
            <div class="link">Projects</div>
          </router-link>
          <a href="">
            <div class="link">Types</div>
          </a>
          <a href="">
            <div class="link">Technologies</div>
          </a>
        </div>
      </div>
      <div class="nav-login d-flex gap-3">
        <a href="">
          <div class="login">Login</div>
        </a>
        <a href="">
          <div class="register">Register</div>
        </a>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.nav-bar {
  height: 70px;
  font-size: 20px;
  .logo {
    a {
      color: #6161ff;
    }
  }
  .link {
    font-size: 18px;
  }
  .nav-login {
    font-size: 18px;
  }
}
</style>
