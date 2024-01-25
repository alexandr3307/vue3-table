<template>
  <MyModal :show="isModalOpened" @close="closeModal">
    <template #title>
      <h3>Добавление пользователя
      </h3>
    </template>
    <template #body>
      <MyInput v-model="row.name" type="text" placeholder="Имя"
               :is-required="true">
      </MyInput>
      <MyInput v-model="row.phone" :maxlength="11" type="number" placeholder="Телефон"
               :is-required="true">
      </MyInput>
      <MySelectDropdown
        v-model="row.master"
        placeholder="Начальник"
        class="converter__dropdown"
        title-key="Name"
        :value="row.master"
        :items="mastersList"
      ></MySelectDropdown>
    </template>
    <template #footer>
      <div class="modal-footer">
        <MyButton @click="addNewRow" :disabled="validate">Добавить</MyButton>
      </div>
    </template>
  </MyModal>
</template>

<script>
import MyModal from '@/components/UI/MyModal'
import MyInput from '@/components/UI/MyInput'
import MyButton from '@/components/UI/MyButton'
import MySelectDropdown from "@/components/UI/MySelectDropdown";
export default {
  name: 'PhonebookModal',
  components: {MySelectDropdown, MyButton, MyInput, MyModal},
  props: {
    isModalOpened: {
      default: false,
      type: Boolean
    },
    mastersList: {
      default: null,
      type: Array
    }
  },
  computed: {
    validate() {
        //лень маску тащить
      return ((!this.row.name || !this.row.phone) || (this.row.phone?.length !== 11));
    },
  },
  data () {
    return {
      row: {
        name: null,
        phone: null,
        master: null,
      }
    }
  },
  methods: {
    closeModal () {
      this.$emit('close')
    },
    addNewRow () {
        this.row.phone = '+' + this.row.phone
        this.$emit('addNewRow', this.row)
    }
  }
}
</script>

<style scoped>
</style>
