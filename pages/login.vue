<template>
  <div class="register">
    <h1 class="text h1">
      Iniciar Sesión
    </h1>
    <form>
      <div class="social">
        <NuxtLink
          class="btn primary"
          to="/home"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="21"
            height="20"
            viewBox="0 0 21 20"
            fill="none"
          >
            <path
              d="M10.5 8.57063V12H16.1719C15.9413 13.4725 14.4569 16.3125 10.5 16.3125C7.08563 16.3125 4.30063 13.4844 4.30063 10C4.30063 6.51562 7.08563 3.6875 10.5 3.6875C12.4413 3.6875 13.7425 4.51562 14.4844 5.23063L17.1994 2.6175C15.4569 0.985 13.1994 0 10.5 0C4.9725 0 0.5 4.4725 0.5 10C0.5 15.5275 4.9725 20 10.5 20C16.2694 20 20.1019 15.9412 20.1019 10.2306C20.1019 9.57438 20.0313 9.07438 19.9456 8.57438L10.5 8.57063Z"
              fill="white"
            />
          </svg>
          Google
        </NuxtLink>
        <NuxtLink
          class="btn primary"
          to="/home"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="23"
            height="20"
            viewBox="0 0 23 20"
            fill="none"
          >
            <path
              d="M22.5 5.85755V15.2672C22.5 15.474 22.4279 15.6478 22.2865 15.7845C22.1443 15.9225 21.9706 15.9912 21.7658 15.9912H14.0905V9.74171L15.5271 10.8456C15.6187 10.9217 15.7325 10.9587 15.8672 10.9587C15.9999 10.9587 16.1157 10.9217 16.2167 10.8449L22.5 5.85755ZM14.0898 4.04311H21.7652C21.9544 4.04311 22.1181 4.09968 22.2528 4.21552C22.3875 4.3307 22.4629 4.48493 22.4757 4.67351L15.8584 9.9505L14.0905 8.55969L14.0898 4.04311ZM12.9846 0V20L0.94751 17.9202V2.13773L12.9866 0.000673546L12.9846 0ZM9.34825 10.0401C9.33007 9.02239 9.0674 8.17916 8.55889 7.51305C8.06049 6.84829 7.41392 6.49739 6.64544 6.46776C5.90525 6.49739 5.27214 6.84762 4.7596 7.51305C4.24773 8.17916 3.99179 9.02374 3.97832 10.0401C3.99179 11.0429 4.2612 11.8781 4.77307 12.5462C5.28561 13.211 5.91737 13.5639 6.65958 13.6023C7.42739 13.5706 8.07329 13.2218 8.58583 12.5516C9.0977 11.8801 9.36711 11.0429 9.38058 10.0401H9.34825ZM6.54643 7.81074C6.9337 7.82893 7.25968 8.04041 7.51899 8.45462C7.77492 8.86883 7.90962 9.39283 7.90962 10.028C7.90962 10.6752 7.7756 11.2019 7.51899 11.6181C7.24891 12.035 6.92629 12.2505 6.53498 12.2505C6.14367 12.2505 5.82106 12.0478 5.55165 11.6309C5.28225 11.214 5.16101 10.688 5.16101 10.0556C5.16101 9.42246 5.28225 8.89645 5.55165 8.49301C5.80691 8.0889 6.13155 7.87338 6.52219 7.84577L6.54643 7.81074Z"
              fill="white"
            />
          </svg>
          Outlook
        </NuxtLink>
      </div>
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
      <div class="actions">
        <NuxtLink class="link">
          Olvide mi contraseña
        </NuxtLink>
        <NuxtLink
          class="btn analogous"
          to="/home"
        >
          Aceptar
        </NuxtLink>
      </div>
    </form>
    <p class="footer">
      No tengo cuenta
      <NuxtLink
        class="link"
        to="/register"
      >
        Registrarme
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
  justify-content: center;
  justify-content: space-between;
  gap: 12px;
  padding: 24px;
  box-sizing: border-box;
  height: 100%;

  form {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .social {
    display: flex;
    padding-bottom: 12px;
    border-bottom: 1px solid var(--GRIS20);
    margin: 0 48px;
    justify-content: space-around;
    margin-bottom: 22px;
  }

  .actions {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .link {
      color: var(--WEB_PRIMARY_900);
    }
  }

  .footer {
    color: var(--GRIS40);

    .link {
      color: var(--WEB_ANALOGOUS1_900);
    }
  }
}
</style>