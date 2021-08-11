<template>
<div class="container">
  <Form @submitForm="onFormSubmit" />
  <TotalBalance :total="totalBalance" />
  <BudgetList :list="list" @deleteItem="onDeleteItem"/>
</div>
</template>

<script>
import BudgetList from '@/components/BudgetList.vue';
import TotalBalance from '@/components/TotalBalance.vue';
import Form from '@/components/Form.vue';

export default {
  name: 'App',
  components: {
    BudgetList,
    TotalBalance,
    Form,
  },
  data: () => ({
    list: {
      1: {
        type: 'INCOME',
        value: 100,
        comment: 'Some comment',
        id: 1,
      },
      2: {
        type: 'OUTCOME',
        value: -50,
        comment: 'Some comment',
        id: 2,
      },
    },
  }),
  computed: {
    totalBalance() {
      return Object.values(this.list).reduce((acc, item) => acc + item.value, 0)
    }
  },
  methods: {
    onDeleteItem(id) {
      delete this.list[id];
    },
    onFormSubmit(data) {
      const newObj = {
        ...data,
        id: String(Math.random()),
      };
      this.list[newObj.id] = newObj;
    },
  }
}
</script>

<style>
body {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  text-decoration: none;
  font-size: 20px;
  line-height: 27px;
}
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding-top: 50px;
}
</style>
