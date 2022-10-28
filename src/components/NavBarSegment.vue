<template>
<nav class="navbar navbar-expand-md">
  <div class="container-fluid">
    <router-link class="navbar-brand pt-0" to="/">
      <img src="@/assets/logo-baner.png" alt="Sube" width="30" height="15">
    </router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link class="nav-link" to="/charge-points">Puntos de carga</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/tas">Terminales TAS</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/data">Información</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/about">Acerca</router-link>
        </li>
      </ul>
    </div>
  </div>
</nav>
</template>

<style scoped>
.navbar {
  background-color: #0072A9;
  font-size: medium;
}

nav .nav-link {
  font-weight: bold;
  color: #E5F0F6;
  padding: 0.2em 1rem;
}

nav .nav-link:hover {
  color: #303030;
}

nav a.router-link-exact-active {
  color: #1d1d1d;
}

.navbar-toggler,
.navbar-toggler-icon {
  padding: 1px !important;
}
</style>