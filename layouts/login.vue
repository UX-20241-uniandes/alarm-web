<template>
  <div class="layout-login">
    <div class="bg" />
    <div class="content">
      <slot />
    </div>
  </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.layout-login {
  display: flex;
  gap: 32px;
  padding: 32px;
  height: 100vh;
  box-sizing: border-box;

  .bg {
    flex: 1;
    background: url("/img/bg.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
  }

  .content {
    flex: 1;
    border: 1px solid var(--GRIS20);
  }
}
</style>