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
              v-model="alarmName"
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
            :disabled="addAlarmDisabled"
            @click="addAlarm"
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
          <p
            v-if="!alarms.length"
            class="text body"
          >
            Ingrese por lo menos una alarma
          </p>
          <div
            v-else
            class="table"
          >
            <div class="head">
              Nombre, Fecha y Hora
            </div>
            <div
              v-for="alarm in alarms"
              :key="alarm.name"
              class="row"
            >
              <div>
                <span>{{ alarm.name }}</span>
                <strong>{{ alarm.date }}</strong>
              </div>
              <button
                class="btn-icon"
                type="button"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="19"
                  viewBox="0 0 16 19"
                  fill="none"
                >
                  <path
                    d="M3 18.7778C2.45 18.7778 1.97917 18.582 1.5875 18.1903C1.19583 17.7987 1 17.3278 1 16.7778V3.77783H0V1.77783H5V0.777832H11V1.77783H16V3.77783H15V16.7778C15 17.3278 14.8042 17.7987 14.4125 18.1903C14.0208 18.582 13.55 18.7778 13 18.7778H3ZM13 3.77783H3V16.7778H13V3.77783ZM5 14.7778H7V5.77783H5V14.7778ZM9 14.7778H11V5.77783H9V14.7778Z"
                    fill="black"
                  />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </div>
      <button
        class="btn analogous lg"
        :disabled="!alarms.length"
        type="button"
        @click="end"
      >
        Guardar Lista
      </button>
    </form>
    <Transition>
      <CustomModal
        v-if="isModalActive"
        title="Creación de alarma"
        width="600"
        height="350"
        :has-footer="true"
      >
        <div class="modal-content">
          <span class="text h1">
            La lista de alarmas fue creada con éxito
          </span>
        </div>

        <template #footer>
          <NuxtLink
            class="btn analogous"
            to="/alarm-list/full"
          >
            Aceptar
          </NuxtLink>
        </template>
      </CustomModal>
    </Transition>
  </div>
</template>


<script setup>
import { ref } from 'vue';
import VueDatePicker from '@vuepic/vue-datepicker';
import dayjs from 'dayjs';
import localizedFormat from 'dayjs/plugin/localizedFormat'
import "dayjs/locale/es";
dayjs.locale("es");
dayjs.extend(localizedFormat)

const date = ref();
const alarmName = ref();
const alarms = ref([]);
const isModalActive = ref(false);
const end = () => {
  isModalActive.value = true;
}
const addAlarm = () => {
  alarms.value.push(
    {
      date: dayjs(date.value).format('lll'),
      name: alarmName.value
    });
  date.value = null;
  alarmName.value = null;
}

const addAlarmDisabled = computed(() => {
  return !date.value || !alarmName.value;
})
</script>

<style lang="scss" scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

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
      align-items: flex-start;
      justify-content: center;
      overflow: auto;
      padding: 10px;
      box-sizing: border-box;

      p {
        align-self: center;
      }
    }

    .table {
      width: 100%;
      max-height: 520px;

      .head {
        padding: 16px 32px;
        background: var(--WEB_ANALOGOUS1_50);
        border-top: 1px solid var(--GRIS60);
        border-bottom: 1px solid var(--GRIS60);
        position: sticky;
        top: 0;
      }

      .row {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 16px 32px;
        border-bottom: 1px solid var(--GRIS20);
        overflow: hidden;
        box-sizing: border-box;

        .btn-icon {
          transition: all 300ms ease-in-out;
          position: relative;
          display: flex;
          align-self: center;
          right: -60px;
        }

        >div {
          display: flex;
          flex-direction: column;

          span {
            font-size: 22px;
          }

          strong {
            font-size: 14px;
          }
        }

        &:hover {
          background: var(--WEB_PRIMARY_50);

          .btn-icon {
            right: 0;
            display: flex;
          }
        }
      }
    }
  }

  .alarm-form {
    display: flex;
    flex-direction: column;
    gap: 16px;

  }

  .btn {
    align-self: flex-end;
  }

  .modal-content {
    flex: 1;
    display: flex;
    flex-direction: column;
    padding: 16px 120px;
    align-items: center;
    justify-content: center;
    text-align: center;
  }
}
</style>