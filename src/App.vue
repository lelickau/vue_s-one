<template>
<div class="container">
  <BudgetList :list="list"/>
</div>
</template>

<script>
import BudgetList from '@/components/BudgetList.vue';

export default {
  name: 'App',
  components: {
    BudgetList,
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
}
</style>
