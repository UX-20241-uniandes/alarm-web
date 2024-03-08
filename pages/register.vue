<template>
  <div class="register">
    <h1 class="text h1">
      Registrarme
    </h1>
    <form>
      <div class="input-group">
        <label
          class="text label"
          for="name"
        >Usuario</label>
        <input
          id="name"
          type="text"
          name="name"
          autocomplete="off"
          placeholder="Ingrese el nombre de usuario"
        >
      </div>
      <div class="input-group">
        <label
          class="text label"
          for="password"
        >Contraseña</label>
        <input
          id="password"
          type="password"
          name="password"
          autocomplete="off"
          placeholder="Ingrese la contraseña"
        >
      </div>
      <div class="input-group">
        <label
          class="text label"
          for="password2"
        >Repetir Contraseña</label>
        <input
          id="password2"
          type="password"
          name="password2"
          autocomplete="off"
          placeholder="Ingrese de nuevo la contraseña"
        >
      </div>
      <div class="actions">
        <NuxtLink
          class="btn analogous"
          to="/home"
        >
          Registrarme
        </NuxtLink>
      </div>
    </form>
    <p class="footer">
      Ya tengo cuenta
      <NuxtLink
        class="link"
        to="/login"
      >
        Iniciar Sesión
      </NuxtLink>
    </p>
  </div>
</template>

<script setup>
definePageMeta({
  layout: 'login'
})
</script>

<style lang="scss" scoped>
.register {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  padding: 24px;
  box-sizing: border-box;
  height: 100%;
  max-width: 550px;
  max-height: 700px;
  width: 100%;

  form {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .actions {
    display: flex;
    justify-content: flex-end;
  }

  .footer {
    color: var(--GRIS40);

    .link {
      color: var(--WEB_ANALOGOUS1_900);
    }
  }
}
</style>