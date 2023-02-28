<script>

import HelloWorldBase from './components/HelloWorldBase.vue';
import DynamicTable from './components/DynamicTable.vue';

export default{
  data() {
  return {
    dynamicTableData:
        {
            headersCount: 3,
            rowsCount: 2,
            headers: ["Header", "Header", "Header"],
            cellsData: [
              ["Cell", "Cell", "Cell"],
              ["Cell", "Cell", "Cell"],
            ],
        },
  }
},
components:{
  HelloWorldBase,
  DynamicTable
}
}
</script>

<template>
  <header>
    <div class="wrapper">
      <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="60" height="60" />
      <HelloWorldBase msg="Vue 3 Dynamic Table" />
    </div>
  </header>

  <main>
    <DynamicTable :tableData="dynamicTableData"/>
  </main>
</template>

<style scoped>
.logo {
  display: block;
  margin: 0 2rem 0 0;
}
</style>
