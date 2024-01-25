<template>
  <input :maxlength="maxlength" :value="modelValue" @input="updateInput" type="text" class="input" :class="[variant, errorClass]" :placeholder="placeholder" />
</template>

<script>
export default {
  name: 'MyInput',
  props: {
    modelValue: [String, Number],
    placeholder: {
      default: '',
      type: String
    },
    isRequired: {
      default: false,
      type: Boolean
    },
    variant: {
      default: 'default',
      type: String
    },
    maxlength: {
      default: null,
      type: Number
    }
  },
  computed: {
    errorClass () {
      return (!this.modelValue && this.isRequired) ? 'errorClass' : 'correctClass'
    }
  },
  methods: {
    updateInput (event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped>
  .default {
    width: 100%;
    max-width: 350px;
    padding: 30px;
    margin-top: 10px;
  }
  .white {
    width: 100%;
    padding: 30px;
    background: #ffffff;
  }
  .errorClass {
    border: red solid 1px;
  }
  .correctClass {
    border: #3EA748 solid 1px;
  }

  input { border-radius: 5px; border: 0; font-size: 16px; color: #9a9a9a; background: #F6F6F6 }
</style>
