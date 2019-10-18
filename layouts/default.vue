<template>
  <div>
    <b-navbar toggleable="sm" type="dark" variant="info">
      <b-navbar-toggle target="nav-text-collapse"></b-navbar-toggle>

      <b-navbar-brand>Vue + Nuxt</b-navbar-brand>

      <b-collapse id="nav-text-collapse" is-nav>
        <b-navbar-nav>
            <b-nav-item to="/">Inicio</b-nav-item>
            <b-nav-item to="/blog">Blog</b-nav-item>
            <b-nav-item to="/images">Imágenes</b-nav-item>
            <b-nav-item to="/nosotros">Nosotros</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <nuxt />
  </div>
</template>
