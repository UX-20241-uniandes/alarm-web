<template>
  <div class="home">
    <img
      src="/img/welcome.jpg"
      alt="Bienvenido"
    >
    <h1 class="text principal">
      Bienvenido a la aplicación de alarmas
    </h1>
    <div class="actions">
      <NuxtLink
        class="btn analogous"
        to="/alarm-list"
      >
        Ir a lista de alarmas
      </NuxtLink>
      <NuxtLink
        class="btn analogous"
        to="/health-recommendations"
      >
        Ir a recomendaciones de salud
      </NuxtLink>
    </div>
  </div>
</template>


<style lang="scss" scoped>
.home {
    display: flex;
    flex-direction: column;
    gap: 32px;
    height: 100%;
    align-items: center;
    justify-content: center;

    img {
        width: 150px;
        height: auto;
    }
    h1 {
        max-width: 360px;
        text-align: center;
    }
    .actions {
        display: flex;
        gap: 50px;
        margin-top: 50px;
        a {
            width: 310px;
        }
    }
}
</style>