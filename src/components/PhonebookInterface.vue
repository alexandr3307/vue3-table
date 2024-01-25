<template>
  <div>
    <div class="phonebook-container">
      <MyButton @click="openModal" >Добавить</MyButton>
      <MyTable :rows="rows"></MyTable>
      <MyButton @click="clearPhonebook" >Очистить книгу</MyButton>
    </div>
    <PhonebookModal v-if="isModalOpened" :isModalOpened="isModalOpened" :mastersList="mastersList" @close="closeModal" @addNewRow="addNewRow" />
  </div>
</template>

<script>
import MyButton from '@/components/UI/MyButton'
import MyTable from '@/components/UI/MyTable'
import PhonebookModal from '@/components/PhonebookInterfaceComponents/PhonebookModal'
export default {
  name: 'PhonebookInterface',
  components: {PhonebookModal, MyTable, MyButton},
  data () {
    return {
      isModalOpened: false,
      rows: [
        {
          name: 'aboba',
          phone: '+79887775544'
        },
        {
          name: 'fefot',
          phone: '+79887775511'
        },
        {
          name: 'fefoasfassfssfasfsfafasfasfafsasfasfafafasft',
          phone: '+79887775511'
        }
      ]
    }
  },
  computed: {
    mastersList() {
      let filteredListOfMasters = this.rows.map((item) => item.name)
        filteredListOfMasters.push('')
      return filteredListOfMasters
    }
  },
  mounted() {
      let localRows = JSON.parse(localStorage.getItem('rows'))
      if (localRows?.length) {
          this.rows = localRows
      }
  },
  watch: {
    rows: {
      handler(val) {
          localStorage.setItem('rows', JSON.stringify(val))
          console.log(JSON.stringify(val))
      },
      deep: true
    }
  },
  methods: {
    openModal () {
      this.isModalOpened = true
    },
    closeModal () {
      this.isModalOpened = false
    },
    addNewRow (row) {
      if (this.rows) {
        this.rows.push(row)
      } else {
          this.rows = row
      }
      this.closeModal()
    },
    clearPhonebook() {
      this.rows = []
      localStorage.setItem('rows', null);
    }
  }
}
</script>

<style scoped>

</style>
