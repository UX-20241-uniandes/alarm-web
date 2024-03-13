<template>
  <div class="full">
    <div class="title">
      <h1 class="text h1">
        Lista Alarmas
      </h1>
      <NuxtLink
        class="btn analogous"
        to="/alarm-list/create"
      >
        Crear Lista de Alarmas
      </NuxtLink>
    </div>
    <div class="text subtitle-h1">
      Seleccione la lista para ver su detalle
    </div>
    <div class="table">
      <div class="head">
        Nombre de la lista de alarmas
      </div>
      <div
        v-for="alarm in alarms"
        :key="alarm.name"
        class="row"
        @click="openModal(alarm)"
      >
        <div>
          {{ alarm.name }}
        </div>
        <button
          class="btn-icon"
          type="button"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
          >
            <path
              d="M5 19H6.425L16.2 9.225L14.775 7.8L5 17.575V19ZM3 21V16.75L16.2 3.575C16.4 3.39167 16.6208 3.25 16.8625 3.15C17.1042 3.05 17.3583 3 17.625 3C17.8917 3 18.15 3.05 18.4 3.15C18.65 3.25 18.8667 3.4 19.05 3.6L20.425 5C20.625 5.18333 20.7708 5.4 20.8625 5.65C20.9542 5.9 21 6.15 21 6.4C21 6.66667 20.9542 6.92083 20.8625 7.1625C20.7708 7.40417 20.625 7.625 20.425 7.825L7.25 21H3ZM15.475 8.525L14.775 7.8L16.2 9.225L15.475 8.525Z"
              fill="black"
            />
          </svg>
        </button>
      </div>
    </div>

    <Transition>
      <CustomModal
        v-if="listDetail"
        title="Detalle"
        :width="550"
        :has-close-button="true"
        :height="660"
        @close="closeModal"
      >
        <div class="modal-content">
          <span class="text h1">
            {{ listDetail.name }}
          </span>
          <div class="summary">
            <div>
              <span class="text label">Código</span>
              <strong>{{ listDetail.code }}</strong>
            </div>
            <div>
              <span class="text label">Fecha Creación</span>
              <strong>{{ listDetail.created }}</strong>
            </div>
            <div class="share">
              <span class="text label">Compartir</span>
              <button
                class="btn-icon"
                @click="activateShare"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="18"
                  height="20"
                  viewBox="0 0 18 20"
                  fill="none"
                >
                  <path
                    d="M15 20C14.1667 20 13.4583 19.7083 12.875 19.125C12.2917 18.5417 12 17.8333 12 17C12 16.8833 12.0083 16.7625 12.025 16.6375C12.0417 16.5125 12.0667 16.4 12.1 16.3L5.05 12.2C4.76667 12.45 4.45 12.6458 4.1 12.7875C3.75 12.9292 3.38333 13 3 13C2.16667 13 1.45833 12.7083 0.875 12.125C0.291667 11.5417 0 10.8333 0 10C0 9.16667 0.291667 8.45833 0.875 7.875C1.45833 7.29167 2.16667 7 3 7C3.38333 7 3.75 7.07083 4.1 7.2125C4.45 7.35417 4.76667 7.55 5.05 7.8L12.1 3.7C12.0667 3.6 12.0417 3.4875 12.025 3.3625C12.0083 3.2375 12 3.11667 12 3C12 2.16667 12.2917 1.45833 12.875 0.875C13.4583 0.291667 14.1667 0 15 0C15.8333 0 16.5417 0.291667 17.125 0.875C17.7083 1.45833 18 2.16667 18 3C18 3.83333 17.7083 4.54167 17.125 5.125C16.5417 5.70833 15.8333 6 15 6C14.6167 6 14.25 5.92917 13.9 5.7875C13.55 5.64583 13.2333 5.45 12.95 5.2L5.9 9.3C5.93333 9.4 5.95833 9.5125 5.975 9.6375C5.99167 9.7625 6 9.88333 6 10C6 10.1167 5.99167 10.2375 5.975 10.3625C5.95833 10.4875 5.93333 10.6 5.9 10.7L12.95 14.8C13.2333 14.55 13.55 14.3542 13.9 14.2125C14.25 14.0708 14.6167 14 15 14C15.8333 14 16.5417 14.2917 17.125 14.875C17.7083 15.4583 18 16.1667 18 17C18 17.8333 17.7083 18.5417 17.125 19.125C16.5417 19.7083 15.8333 20 15 20ZM15 4C15.2833 4 15.5208 3.90417 15.7125 3.7125C15.9042 3.52083 16 3.28333 16 3C16 2.71667 15.9042 2.47917 15.7125 2.2875C15.5208 2.09583 15.2833 2 15 2C14.7167 2 14.4792 2.09583 14.2875 2.2875C14.0958 2.47917 14 2.71667 14 3C14 3.28333 14.0958 3.52083 14.2875 3.7125C14.4792 3.90417 14.7167 4 15 4ZM3 11C3.28333 11 3.52083 10.9042 3.7125 10.7125C3.90417 10.5208 4 10.2833 4 10C4 9.71667 3.90417 9.47917 3.7125 9.2875C3.52083 9.09583 3.28333 9 3 9C2.71667 9 2.47917 9.09583 2.2875 9.2875C2.09583 9.47917 2 9.71667 2 10C2 10.2833 2.09583 10.5208 2.2875 10.7125C2.47917 10.9042 2.71667 11 3 11ZM15 18C15.2833 18 15.5208 17.9042 15.7125 17.7125C15.9042 17.5208 16 17.2833 16 17C16 16.7167 15.9042 16.4792 15.7125 16.2875C15.5208 16.0958 15.2833 16 15 16C14.7167 16 14.4792 16.0958 14.2875 16.2875C14.0958 16.4792 14 16.7167 14 17C14 17.2833 14.0958 17.5208 14.2875 17.7125C14.4792 17.9042 14.7167 18 15 18Z"
                    fill="#666666"
                  />
                </svg>
              </button>
              <Transition>
                <div
                  v-if="isActiveShare"
                  class="share-list"
                >
                  <div>
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="32"
                      height="32"
                      viewBox="0 0 32 32"
                      fill="none"
                    >
                      <g clip-path="url(#clip0_4162_454)">
                        <path
                          d="M27.2811 4.65C24.2871 1.65 20.3061 0 16.0621 0C7.32405 0 0.212055 7.112 0.212055 15.856C0.212055 18.65 0.943055 21.381 2.33105 23.781L0.0810547 32L8.48705 29.794C10.8061 31.056 13.4121 31.725 16.0621 31.725H16.0681C24.8061 31.725 31.9241 24.612 31.9241 15.869C31.9241 11.631 30.2751 7.65 27.2811 4.65ZM16.0691 29.05C13.7001 29.05 11.3811 28.413 9.35605 27.213L8.87505 26.925L3.88805 28.231L5.21905 23.368L4.90605 22.868C3.58105 20.774 2.88705 18.349 2.88705 15.856C2.88705 8.587 8.79906 2.675 16.0751 2.675C19.5941 2.675 22.9061 4.05 25.3941 6.537C27.8821 9.031 29.2501 12.337 29.2501 15.862C29.2441 23.137 23.3311 29.05 16.0691 29.05ZM23.2941 19.175C22.9001 18.975 20.9501 18.019 20.5881 17.887C20.2261 17.755 19.9631 17.687 19.6941 18.087C19.4321 18.481 18.6691 19.375 18.4381 19.643C18.2071 19.905 17.9761 19.943 17.5821 19.743C17.1881 19.543 15.9071 19.124 14.3941 17.774C13.2191 16.724 12.4191 15.424 12.1881 15.03C11.9571 14.636 12.1631 14.417 12.3631 14.224C12.5441 14.049 12.7571 13.761 12.9571 13.53C13.1571 13.299 13.2191 13.136 13.3511 12.868C13.4821 12.606 13.4201 12.374 13.3201 12.174C13.2201 11.974 12.4261 10.024 12.1011 9.23C11.7821 8.455 11.4511 8.561 11.2071 8.549C10.9761 8.537 10.7131 8.537 10.4511 8.537C10.1891 8.537 9.75706 8.637 9.39505 9.031C9.03205 9.425 8.00806 10.387 8.00806 12.337C8.00806 14.287 9.42705 16.168 9.62705 16.437C9.82705 16.699 12.4211 20.706 16.3961 22.418C17.3401 22.824 18.0771 23.068 18.6521 23.255C19.6021 23.555 20.4651 23.511 21.1461 23.411C21.9081 23.298 23.4901 22.455 23.8211 21.53C24.1521 20.605 24.1521 19.811 24.0521 19.649C23.9581 19.474 23.6961 19.374 23.2961 19.174L23.2941 19.175Z"
                          fill="#568792"
                        />
                      </g>
                      <defs>
                        <clipPath id="clip0_4162_454">
                          <rect
                            width="32"
                            height="32"
                            fill="white"
                          />
                        </clipPath>
                      </defs>
                    </svg>
                    <span>Whatsapp</span>
                  </div>
                  <div>
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="32"
                      height="32"
                      viewBox="0 0 32 32"
                      fill="none"
                    >
                      <path
                        d="M12 12H17.535V14.837H17.614C18.384 13.456 20.269 12 23.078 12C28.92 12 30 15.637 30 20.367V30H24.231V21.46C24.231 19.423 24.189 16.803 21.23 16.803C18.225 16.803 17.767 19.021 17.767 21.312V30H12V12Z"
                        fill="#568792"
                      />
                      <path
                        d="M2 12H8V30H2V12Z"
                        fill="#568792"
                      />
                      <path
                        d="M8 7C8 8.657 6.657 10 5 10C3.343 10 2 8.657 2 7C2 5.343 3.343 4 5 4C6.657 4 8 5.343 8 7Z"
                        fill="#568792"
                      />
                    </svg>
                    <span>LinkedIn</span>
                  </div>
                  <div>
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="32"
                      height="32"
                      viewBox="0 0 32 32"
                      fill="none"
                    >
                      <path
                        d="M19 6H24V0H19C15.14 0 12 3.14 12 7V10H8V16H12V32H18V16H23L24 10H18V7C18 6.458 18.458 6 19 6Z"
                        fill="#568792"
                      />
                    </svg>
                    <span>Facebook</span>
                  </div>
                  <div>
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="32"
                      height="32"
                      viewBox="0 0 32 32"
                      fill="none"
                    >
                      <path
                        d="M24.3249 3H28.7359L19.0999 14.013L30.4359 29H21.5599L14.6079 19.911L6.65287 29H2.23987L12.5469 17.22L1.67188 3H10.7729L17.0569 11.308L24.3249 3ZM22.7769 26.36H25.2209L9.44487 5.501H6.82188L22.7769 26.36Z"
                        fill="#568792"
                      />
                    </svg>
                    <span>x</span>
                  </div>
                  <div>
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="32"
                      height="32"
                      viewBox="0 0 32 32"
                      fill="none"
                    >
                      <path
                        d="M28 5H4C1.791 5 0 6.792 0 9V22C0 24.209 1.791 26 4 26H28C30.209 26 32 24.209 32 22V9C32 6.792 30.209 5 28 5ZM2 10.25L8.999 15.5L2 20.75V10.25ZM30 22C30 23.104 29.102 24 28 24H4C2.897 24 2 23.104 2 22L9.832 16.125L14.2 19.402C14.733 19.8 15.366 20.002 16 20.002C16.633 20.002 17.266 19.801 17.799 19.402L22.168 16.125L30 22ZM30 20.75L23 15.5L30 10.25V20.75ZM17.199 18.602C16.85 18.864 16.436 19.002 16 19.002C15.564 19.002 15.149 18.863 14.8 18.602L2 9C2 7.897 2.897 7 4 7H28C29.102 7 30 7.897 30 9L17.199 18.602Z"
                        fill="#568792"
                      />
                    </svg>
                    <span>Email</span>
                  </div>
                </div>
              </Transition>
            </div>
          </div>
          <div class="text h2">
            Alarmas
          </div>
          <div class="table">
            <div class="head">
              Nombre, Fecha y Hora
            </div>
            <div
              v-for="alarm in listDetail.alarms"
              :key="alarm.name"
              class="row"
            >
              <div>
                <span>{{ alarm.name }}</span>
                <strong>{{ alarm.date }}</strong>
              </div>
            </div>
          </div>
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
import jsonData from '~/assets/json/alarms.json';
const alarms = ref(jsonData)
const listDetail = ref(null);
const isActiveShare = ref(false);
const openModal = (detail) => {
  listDetail.value = detail;
}
const closeModal = () => {
  listDetail.value = null;
  isActiveShare.value = false;
}
const activateShare = () => {
  isActiveShare.value = !isActiveShare.value;
}
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

.full {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.title {
  display: flex;
  align-items: center;
  justify-content: space-between;
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

.modal-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 16px 24px;
  justify-content: flex-start;
  box-sizing: border-box;
  height: calc(100% - 42px);

  .summary {
    display: grid;
    grid-template-columns: auto 1fr auto;
    gap: 24px;

    >div {
      padding: 14px 0;
      display: flex;
      flex-direction: column;
      gap: 8px;

      &.share {
        position: relative;
        align-items: center;
      }

      strong {
        font-size: 16px;
        line-height: 20px;
      }

      .share-list {
        z-index: 1;
        background: var(--BLANCO);
        position: absolute;
        top: 100%;
        right: 0;
        width: 320px;
        border-radius: 8px;
        border: 1px solid var(--WEB_SECONDARY_600);

        >div {
          padding: 16px 24px;
          border-bottom: 1px solid var(--WEB_SECONDARY_600);
          display: flex;
          gap: 20px;
          align-items: center;

          &:last-child {
            border: none;
          }

          >span {
            color: var(--WEB_PRIMARY_800);
            font-weight: 500;
            font-size: 18px;
          }
        }
      }
    }
  }

  .table {
    overflow: auto;
  }
}
</style>