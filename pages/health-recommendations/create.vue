<template>
  <div class="container">
    <div class="title">
      <h1 class="text h1">
        Crear Recomendación
      </h1>
      <NuxtLink
        class="link"
        to="/health-recommendations"
      >
        &lt; Volver
      </NuxtLink>
    </div>

    <form>
      <div class="ia">
      <button class="btn analogous lg" type="button" @click="endIa">
        Obtener una recomendación de la IA
      </button>
    </div>
      <div class="input-group">
        <label
          class="text label"
          for="name"
        >Titulo</label>
        <input
          id="name"
          type="text"
          name="name"
          autocomplete="off"
          placeholder="Ingrese el nombre de la recomendación de salud"
        >
      </div>

      <div class="healths">
        <div class="input-imagen">
          <label class="text h2">Imagen</label>
          <div class="imagen">
            <img src="/public/img/Nube.png" alt="">
            <button class="btn primary">
              Elegir una imagen
            </button>
            <label class="text body">Arrastre y suelte la imagen</label>
          </div>
        </div>
        <div class="health-form">
          <div class="input-recomend">
            <label class="text h2">Recomendación</label>
            <textarea
              type="text"
              placeholder="Por favor ingrese la recomendación"
              class="full-width full-height"
            ></textarea>
          </div>
        </div>
        
      </div>
      <button
        class="btn analogous lg guardar"
        type="button"
        @click="end">
        Guardar Lista
      </button>
    </form>
    <Transition>
      <CustomModal v-if="isModalCreateActive"
        title="Creación de recomendación Exitosa"
        :width="600"
        :height="350"
        :has-footer="true" >
        <div class="modal-content-sucess">
          <span class="text h1">
            La recomendación de salud fue creada con éxito
          </span>
        </div>

        <template #footer>
          <NuxtLink class="btn analogous" to="/health-recommendations/list" >
            Aceptar
          </NuxtLink>
        </template>
      </CustomModal>
    </Transition>

    <Transition>
      <CustomModal v-if="isModalIaActive"
        title="Recomendación por IA"
        :width="770"
        :height="530"
        :has-footer="true"
        :has-close-button="true"
      >
      <div class="modal-content">
        <span class="text label">
          Título
        </span>
        <span class="text negrita">
          10 minutos de estiramiento diario
        </span>
        <div class="content">
          <div>
            <span class="text label">Imagen</span>
            <img class ="modal-img" src="/public/img/bg.jpg" alt="">
          </div>
          <div>
            <span class="text label">Recomendación</span>
            <span class="text body">
              Dedica al menos 10 minutos cada día para realizar una serie de estiramientos suaves. 
              Los estiramientos ayudan a mejorar la flexibilidad muscular, reducen la rigidez y mejoran la circulación sanguínea. 
              Además, pueden aliviar el estrés y la tensión acumulados en el cuerpo, lo que te hará sentir más relajado y rejuvenecido.
            </span>
          </div>
        </div>
      </div>

        <template #footer>
          <a class="link" @click="closeIa">
            Cancelar
          </a>
          <button class="btn analogous" @click="end">
          Usar esta recomendación
        </button>
        </template>
      </CustomModal>
    </Transition>
  </div>
</template>
    
<script setup>
  const isModalIaActive = ref(false);
  const endIa = () => {
    isModalIaActive.value = true;
  }

  const closeIa = () => {
    isModalIaActive.value = false;
  }

  
  const isModalCreateActive = ref(false);
  const end = () => {
    isModalIaActive.value = false;
    isModalCreateActive.value = true;
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

    .ia{
      button{
        width: 100%;
      }
    }
  }

  h2 {
    margin-top: 16px;
    border-bottom: 1px solid var(--GRIS20);
    padding-bottom: 8px;
  }

  .healths {
    display: grid;
    gap: 24px;
    grid-template-columns: 1fr 1fr;

    .input-imagen{
      padding: 10px 0px;

      .imagen{
        display: flex;
        flex-wrap: nowrap;
        flex-direction: column;
        align-items: center;
        gap: 15px;

        border: 1px solid var(--GRIS20);
        padding: 100px 20px;

        img{
        width: 120px;
        }
      }
    }
  }

  .health-form {
    display: flex;
    flex-direction: column;
    gap: 16px;

    .input-recomend{
      position: relative;
      width: 100%;
      height: 100%;
      padding: 10px; 

      textarea {
        width: calc(100% - 30px); 
        height: calc(100% - 53px); 
        border: 1px solid var(--GRIS20);
        padding: 10px; 
        resize: none;
        padding: 10px; 
      }

      textarea:focus {
        outline: none; 
      }
    }

  }

  .guardar {
    align-self: flex-end;
    margin-bottom: 20px;
  }

  .modal-content-sucess {
    flex: 1;
    display: flex;
    flex-direction: column;
    padding: 16px 100px;
    align-items: center;
    justify-content: center;
    text-align: center;
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
  .link{
    cursor: pointer; 
    color: var(--WEB_PRIMARY_900);
  }
}
</style>