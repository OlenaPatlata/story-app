<template>
  <header class="main-header">
    <nav class="main-nav">
      <ul class="nav-links">
        <nuxt-link to="/blog" tag="li" class="nav-link"><a>All posts</a></nuxt-link>
        <nuxt-link to="/about" tag="li" class="nav-link"
          ><a>About</a></nuxt-link
        >
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'TheHeader',
}
</script>

<style scoped>
.main-header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background: #022d30;
  height: 4.5rem;
}

.main-nav {
  height: 100%;
}

.nav-links {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.nav-link {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 1rem;
  padding: 0.3rem;
}

.nav-link.nuxt-link-exact-active {
  border-bottom: 3px solid palevioletred;
}

.nav-link a {
  display: block;
  color: azure;
}

.nav-link a:hover,
.nav-link a:active,
.nav-link a:focus,
.nav-link.nuxt-link-exact-active a {
  color: palevioletred;
}
</style>
