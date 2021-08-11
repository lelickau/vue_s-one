<template>
  <div class="budget-list-wrap">
    <ElCard :header="header">
      <template v-if="!isEmpty">
        <div class="list-item" v-for="(item, prop) in list" :key="prop">
          <span class="budget-comment">{{item.comment}}</span>
          <span class="budget-value">{{item.value}}</span>
          <ElButton type="danger" size="mini" @click="deleteItem(item.id)">Удалить</ElButton>
        </div>
      </template>
      <ElAlert v-else type="info" :title="emptyTitle" :closable="false" ></ElAlert>
    </ElCard>
  </div>
</template>

<script>
export default {
  name: 'BudgetList',
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
  methods: {
    deleteItem(id) {
      this.$emit('deleteItem', id);
    }
  }
}
</script>

<style scoped>
.budget-list-wrap {
  max-width: 900px;
  margin: 0 auto;
  margin-top: 25px;
}
.list-item {
  display: flex;
  align-items: center;
  padding: 10px 15px;
}
.budget-value {
  margin-right: 20px;
  margin-left: auto;
  font-weight: bold;
}
</style>