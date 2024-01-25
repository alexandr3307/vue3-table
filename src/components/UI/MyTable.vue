<template>
<div class="table">
<!--  Заголовки-->
  <MyTableRow :row="headlines" :isHeadline="true"></MyTableRow>
  <TransitionGroup name="list" tag="div">
    <div v-for="(row, index) in rows" :key="index">
      <MyTableRow :row="getArrayRow(row)" />
    </div>
  </TransitionGroup>
</div>
</template>

<script>
import MyTableRow from '@/components/UI/MyTableRow'
export default {
  name: 'MyTable',
  components: {MyTableRow},
  props: {
    rows: {
      type: Array,
      require: true
    }
  },
  data () {
    return {
      headlines: [
        'Имя',
        'Телефон'
      ]
    }
  },
  methods: {
    // сомнительное решение, однако я не хотел чтобы строка таблицы зависила от ключа
    getArrayRow (row) {
      let rowTemporaryVariable = Object.assign({}, row)
      delete rowTemporaryVariable.master
      return Object.keys(rowTemporaryVariable).map(function (key) { return rowTemporaryVariable[key] })
    }
  }
}
</script>

<style scoped>
  .table {
    display: flex;
    flex-direction: column;
    margin: 10px auto;
    padding: 5px;
  }
  .list-enter-active,
  .list-leave-active {
    transition: all 0.5s ease;
  }
  .list-enter-from,
  .list-leave-to {
    opacity: 0;
    transform: translateX(30px);
  }
</style>
