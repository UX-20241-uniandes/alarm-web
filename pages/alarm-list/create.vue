<template>
  <div class="container">
    <div class="title">
      <h1 class="text h1">
        Crear Lista de Alarmas
      </h1>
      <NuxtLink
        class="link"
        to="/alarm-list"
      >
        &lt; Volver
      </NuxtLink>
    </div>

    <form>
      <div class="input-group">
        <label
          class="text label"
          for="name"
        >Nombre</label>
        <input
          id="name"
          type="text"
          name="name"
          autocomplete="off"
          placeholder="Ingrese el nombre de la lista de alarmas"
        >
      </div>
      <h2 class="text h2">
        Alarmas
      </h2>
      <div class="alarms">
        <div class="alarm-form">
          <div class="input-group">
            <label
              class="text label"
              for="alarmname"
            >Nombre</label>
            <input
              id="alarmname"
              type="text"
              name="alarmname"
              autocomplete="off"
              placeholder="Ingrese el nombre de la alarma"
            >
          </div>
          <div class="input-group">
            <label
              class="text label"
              for="name"
            >Nombre</label>
            <VueDatePicker
              v-model="date"
              :inline="{ input: true }"
              text-input
              auto-apply
            />
          </div>
          <button
            type="button"
            class="btn primary"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="21"
              height="20"
              viewBox="0 0 21 20"
              fill="none"
            >
              <path
                d="M7.77718 20L0.666992 10.5198L2.44454 8.14969L7.77718 15.2599L19.2221 0L20.9996 2.37006L7.77718 20Z"
                fill="white"
              />
            </svg> Agregar
          </button>
        </div>
        <div class="detail">
          <p class="text body">
            Ingrese por lo menos una alarma
          </p>
        </div>
      </div>
      <button
        class="btn analogous lg"
        disabled
      >
        Guardar Lista
      </button>
    </form>

    <NuxtLink to="/alarm-list/list">
      Lista Llena
    </NuxtLink>
  </div>
</template>


<script setup>
import { ref } from 'vue';
import VueDatePicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css'

const date = ref();
</script>

<style lang="scss" scoped>
.container {
    display: flex;
    flex-direction: column;
    gap: 32px;

    .title {
        display: flex;
        padding-bottom: 8px;
        justify-content: space-between;
        align-items: center;
        align-self: stretch;
        border-bottom: 1px solid var(--GRIS20);
    }

    form {
        display: flex;
        flex-direction: column;
        gap: 16px;
        margin: 0 120px;
    }

    h2 {
        margin-top: 16px;
        border-bottom: 1px solid var(--GRIS20);
        padding-bottom: 8px;
    }

    .alarms {
        display: grid;
        gap: 24px;
        grid-template-columns: 318px 1fr;

        .detail {
            border: 1px solid var(--GRIS20);
            display: flex;
            align-items: center;
            justify-content: center;
        }
    }

    .alarm-form {
        display: flex;
        flex-direction: column;
        gap: 16px;

    }

    button {
        align-self: flex-end;
    }
}
</style>