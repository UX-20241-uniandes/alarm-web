<template>
  <div class="container">
    <img
      src="/img/welcome.jpg"
      alt="Bienvenido"
    >
    <h1 class="text principal">
      Administrador de Alarmas
    </h1>
    <p class="text body">
      Optimiza tu jornada laboral con nuestra herramienta de gestión de alarmas saludables. Personaliza los
      recordatorios para pausas activas, ajusta la frecuencia, comparte y permite que los colaboradores de tu empresa se
      mantengan saludables y activos.
    </p>
    <div class="actions">
      <NuxtLink
        class="btn analogous"
        to="/login"
      >
        Iniciar Sesión
      </NuxtLink>
      <NuxtLink
        class="btn primary"
        to="/register"
      >
        Registrarse
      </NuxtLink>
    </div>
  </div>
</template>

<script setup>
definePageMeta({
  layout: 'empty'
})
</script>

<style lang="scss" scoped>
.container {
  max-width: 1024px;
  margin: 0 auto;
  padding: 32px;
  display: flex;
  flex-direction: column;
  gap: 32px;
  height: 100vh;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;

  img {
    width: 150px;
    height: auto;
  }

  p {
    text-align: center;
  }

  h1 {
    text-align: center;
  }

  .actions {
    display: flex;
    gap: 50px;
    width: 100%;
    justify-content: space-evenly;
  }
}
</style>