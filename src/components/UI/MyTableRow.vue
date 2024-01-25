<template>
    <div class="row">
      <div v-for="(string, index) in row" :key="index" class="item" :class="isHeadline ? 'headline' : ''">
        {{ string }}
      </div>
  </div>
</template>

<script>
export default {
  name: 'MyTableRow',
  props: {
    row: {
      required: true,
      type: Array
    },
    isHeadline: {
      default: false,
      type: Boolean
    }
  }
}
</script>

<style scoped>
.row {
  display: flex;
  width: 100%;
  justify-content: center;
}
.item {
  border: 1px solid black;
  padding: 5px 20px;
  width: 175px;
  white-space: normal;
  word-break: break-all;
}
  .headline {
    font-weight: bold;
    font-size: 20px;
  }
</style>
