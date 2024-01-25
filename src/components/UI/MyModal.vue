<template>
  <div class="modal-shadow" @click.self="closeModal">
    <div class="modal">
      <div class="modal-close" @click="closeModal">&#10006;</div>
      <slot name="title">
        <h3 class="modal-title">Заголовок</h3>
      </slot>
      <slot name="body">
      </slot>
      <slot name="footer">
      </slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MyModal',
  props: {
    show: {
      default: false,
      type: Boolean
    }
  },
  methods: {
    closeModal () {
      this.$emit('close')
    }
  }
}
</script>

<style scoped>
  .modal-shadow {
    position: absolute;
    top: 0;
    left: 0;
    min-height: 100%;
    width: 100%;
    background: rgba(0, 0, 0, 0.39);
  }

  .modal {
    background: #fff;
    border-radius: 8px;
    padding: 15px;
    min-width: 420px;
    max-width: 480px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

    .modal-close {
      border-radius: 50%;
      color: #fff;
      background: #3EA748;
      display: flex;
      align-items: center;
      justify-content: center;
      position: absolute;
      top: 7px;
      right: 7px;
      width: 30px;
      height: 30px;
      cursor: pointer;
    }

  .modal-title {
      color: #3EA748;
    }

    .modal-content {
      margin-bottom: 20px
    }
  .modal-footer__button {
    background-color: #3EA748;
    color: #fff;
    border: none;
    text-align: center;
    padding: 8px;
    font-size: 17px;
    font-weight: 500;
    border-radius: 8px;
    min-width: 150px;
  }
</style>
