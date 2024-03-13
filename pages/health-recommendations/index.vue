<template>
  <div class="container">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="108"
      height="108"
      viewBox="0 0 108 108"
      fill="none"
    >
      <path
        fill-rule="evenodd"
        clip-rule="evenodd"
        d="M54 0.5C24.468 0.5 0.5 24.468 0.5 54C0.5 83.532 24.468 107.5 54 107.5C83.532 107.5 107.5 83.532 107.5 54C107.5 24.468 83.532 0.5 54 0.5ZM48.65 80.75V70.05H59.35V80.75H48.65ZM48.65 27.25V59.35H59.35V27.25H48.65Z"
        fill="#CCCCCC"
      />
    </svg>
    <h1 class="text h1">
      Lista Recomendaciones Salud Vacía
    </h1>
    <p class="text subtitle-h1">
      Aún no has creado ninguna recomendación de salud
    </p>
    <NuxtLink
      class="btn analogous"
      to="/health-recommendations/create"
    >
      Crear Recomendación de Salud
    </NuxtLink>
  </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.container {
    display: flex;
    flex-direction: column;
    gap: 50px;
    height: 100%;
    align-items: center;
    justify-content: center;
}
</style>