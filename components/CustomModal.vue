<template>
  <div>
    <div class="overlay">
      <div
        class="modal"
        :style="{width: width + 'px', height: height + 'px'}"
      >
        <div class="header">
          {{ title }}
          <button
            class="btn-icon"
            @click="$emit('close')"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="21"
              height="20"
              viewBox="0 0 21 20"
              fill="none"
            >
              <path
                d="M2.26474 20L0.26474 18L8.26474 10L0.26474 2L2.26474 0L10.2647 8L18.2647 0L20.2647 2L12.2647 10L20.2647 18L18.2647 20L10.2647 12L2.26474 20Z"
                fill="#666666"
              />
            </svg>
          </button>
        </div>
        <slot />
        <div
          v-if="hasFooter"
          class="footer"
        >
          <slot name="footer" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineEmits(['close'])
defineProps({
    title: {
        type: String,
        default: ''
    },
    width: {
        type: Number,
        default: 400
    },
    height: {
        type: Number,
        default: 300
    },
    hasCloseButton: Boolean,
    hasFooter: Boolean
})

</script>

<style lang="scss" scoped>
.overlay {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: #00000077;
}

.modal {
    display: flex;
    flex-direction: column;
    border: 1px solid var(--GRIS80);
    border-radius: 8px;
    min-width: 400px;
    min-height: 300px;
    background: var(--BLANCO);
    box-sizing: border-box;

    .header {
        flex: 0;
        border-radius: 8px 8px 0 0;
        display: flex;
        padding: 8px 16px;
        align-items: center;
        justify-content: space-between;
        border-bottom: 1px solid var(--GRIS60);
        background: var(--WEB_ANALOGOUS1_50);
        button {
          display: flex;
          padding: 0;
        }
    }

    .footer {
        flex: 0;
        border-radius: 0 0 8px 8px;
        display: flex;
        padding: 8px 16px;
        align-items: center;
        justify-content: flex-end;
        border-top: 1px solid var(--GRIS60);
    }
}
</style>