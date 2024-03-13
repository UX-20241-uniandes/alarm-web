<template>
  <div class="full">
    <div class="title">
      <h1 class="text h1">
        Lista Recomendaciones
      </h1>
      <NuxtLink
        class="btn analogous"
        to="/health-recommendations/create"
      >
      Crear nueva recomendación de salud
      </NuxtLink>
    </div>
    <div class="text subtitle-h1">
      Seleccione la lista para ver su detalle
    </div>
    <div class="table">
      <div class="head">
        Nombre de la recomendación de salud
      </div>
      <div
        v-for="recomendacion in recomendaciones"
        :key="recomendacion.titulo"
        class="row"
        @click="openModal(recomendacion)"
      >
        <div>
          {{ recomendacion.titulo }}
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
        title="Detalle Recomendación"
        :has-close-button="true"
        :width="770"
        :height="500"
        @close="closeModal"
      >
        <div class="modal-content">
          <span class="text label">
            Título
          </span>
          <span class="text negrita">
            {{ listDetail.titulo }}
          </span>
          <div class="content">
            <div>
              <span class="text label">Imagen</span>
              <img class ="modal-img" src="/public/img/bg.jpg" alt="">
            </div>
            <div>
              <span class="text label">Recomendación</span>
              <span class="text body">{{ listDetail.recomendacion }}</span>
            </div>
          </div>
        </div>
      </CustomModal>
    </Transition>
  </div>
</template>
      
<script setup>
  import jsonData from '~/assets/json/recomendaciones.json';
  const recomendaciones = ref(jsonData)
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
  height: calc(100% - 62px);

  .content {
    display: grid;
    grid-template-columns: auto 1fr auto;
    gap: 70px;

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

      img {
        width: 250px;
      }
    }
  }

  .table {
    overflow: auto;
  }
}
</style>