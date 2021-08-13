<template>
  <div class="budget-list-wrap">
    <ElCard :header="header">
      <div v-if="!isEmpty">
        <BudgetItem @deleteItem="$emit('deleteItem', item)" v-for="item in list" :key="item.id" :item="item"></BudgetItem>
      </div>
      <ElAlert v-else type="info" :title="emptyTitle" :closable="false" ></ElAlert>
    </ElCard>
  </div>
</template>

<script>
import BudgetItem from '@/components/BudgetItem.vue';
export default {
  name: 'BudgetList',
  components: {
    BudgetItem,
  },
  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },
  data: () => ({
    header: 'Список бюджета',
    emptyTitle: 'Список бюджета пустой',
  }),
  computed: {
    isEmpty() {
      return !Object.keys(this.list).length;
    },
  },

}
</script>

<style scoped>

</style>