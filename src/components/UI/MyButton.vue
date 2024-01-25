<template>
  <button class="btn" :class="[variant, size, disabled ? 'disabled' : '']" :disabled=disabled>
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'MyButton',
  props: {
    variant: {
      default: 'default',
      type: String
    },
    size: {
      default: 'lg',
      type: String
    },
    disabled: {
      default: false,
      type: Boolean
    }
  }
}
</script>

<style scoped lang="scss">
  .btn {
    cursor: pointer;
    border-radius: 10px;
    height: fit-content;
    margin-top: 10px;
    &:active {
      transform: scale(1.1);
    }
  }
  .lg {
    width: 160px;
    height: 50px;
  }
  .sm {
    padding: 15px 20px;
    font-size: 16px;

  }
  .sm1 {
    padding: 12px 43px;
  }
  .default {
    border: none;
    color: #ffffff;
    background: #3EA748;
  }
  .outline {
    color: #3EA748;
    border: 1px solid #3EA748;
    background: #ffffff;
  }
  .simple {
    color: #3EA748;
    background: #ffffff;
    border: none;
  }
  .outline-dashed {
    color: #3EA748;
    border: 1px dashed #3EA748;
    background: #ffffff;
    align-items: center;
    display: flex;
    justify-content: space-between;
    width: 100%;
    padding: 30px;
    font-size: 16px;
    height: 71px;
    margin-top: 30px;
  }

  .disabled {
    cursor: default;
    background: lightgrey;
  }
</style>
