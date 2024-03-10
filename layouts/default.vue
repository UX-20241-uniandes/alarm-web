<template>
  <div>
    <header>
      <div class="container">
        <NuxtLink
          class="menu-item"
          to="/home"
        >
          <img
            src="/img/logo.png"
            alt="Logo"
          >
        </NuxtLink>
        <NuxtLink
          class="menu-item"
          to="/home"
        >
          Inicio
        </NuxtLink>
        <NuxtLink
          class="menu-item"
          to="/alarm-list"
        >
          Lista de alarmas
        </NuxtLink>
        <NuxtLink
          class="menu-item"
          to="/health-recommendations"
        >
          Recomendaciones de salud
        </NuxtLink>
        <hr>
        <NuxtLink
          class="btn primary"
          to="/"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            viewBox="0 0 20 20"
            fill="none"
          >
            <path
              d="M2.22222 20C1.61111 20 1.08796 19.7824 0.652778 19.3472C0.217593 18.912 0 18.3889 0 17.7778V2.22222C0 1.61111 0.217593 1.08796 0.652778 0.652778C1.08796 0.217593 1.61111 0 2.22222 0H10V2.22222H2.22222V17.7778H10V20H2.22222ZM14.4444 15.5556L12.9167 13.9444L15.75 11.1111H6.66667V8.88889H15.75L12.9167 6.05556L14.4444 4.44444L20 10L14.4444 15.5556Z"
            />
          </svg> Cerrar sesión
        </NuxtLink>
      </div>
    </header>
    <main>
      <slot />
    </main>
  </div>
</template>

<style lang="scss">
header {
  position: sticky;
  top: 0;
  height: 56px;

  border-bottom: 1px solid var(--WEB_PRIMARY_50);
  background: var(--WEB_PRIMARY_800);
  box-sizing: border-box;

  .container {
    margin: 0 auto;
    display: flex;
    align-items: center;
    gap: 18px;
    flex-shrink: 0;
    align-self: stretch;
    max-width: 1400px;
  }

  img {
    height: 48px;
    width: auto;
  }

  hr {
    flex: 1;
    border: none;
  }

  .menu-item {
    color: var(--BLANCO);
    font-size: 18px;
    line-height: 22px;
    font-weight: 300;

    &.router-link-active {
      font-weight: 600;

    }
  }
}

main {
  max-width: 1200px;
  height: calc(100vh - 56px);
  margin: 32px auto;
  padding: 0 32px;
  box-sizing: border-box;
}
</style>