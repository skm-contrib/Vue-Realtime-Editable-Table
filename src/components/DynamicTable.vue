<template lang="">
  
  <div class="tableContainer">
    <table>
      <thead>
        <tr>
          <th v-for="i in tableData.headersCount" :key="i">
            <button class="removeBtn" @click="removeColumn(i-1)">✖ Delete column</button>
          </th>
          
          <div class="functionalBtns">
            <button class="addButton" @click="addColumn">+ Add column</button>
          </div>
                
        </tr>
            
        <tr>
          <th v-for="i in tableData.headersCount" :key="i">
            <input class="cellDataInputHeader" v-model="tableData.headers[i-1]"/>
          </th>
          </tr>
      </thead>

      <tbody class="">
        <tr v-for="(row, idx1) in tableData.cellsData">
          <td class="table-success" v-for="(col, idx2) in tableData.headers">
            <input v-model="tableData.cellsData[idx1][idx2]" type="text" class="cellDataInput"/>
          </td>
                
          <div class="functionalBtns">
            <button class="removeBtn" @click="removeRow(idx1)">✖ Delete row</button>
          </div>
          
        </tr>
      </tbody>
    </table>
    
    <button class="addButton" @click="addRow">+ Add row</button>
  </div>

</template>

<script>
export default {
  props: {
    tableData: Array,
  },
  data() {
    return {
      newRow: [],
    };
  },
  methods: {
    addColumn() {
      this.tableData.headersCount += 1;
      this.tableData.headers.push("Header");
      let cycleRange = this.tableData.rowsCount;
      
      for (let i = 0; i < cycleRange; i++) {
        console.log('added');
        this.tableData.cellsData[i].push("Cell");
      }
    },
    removeColumn(index) {
      if ( this.tableData.headersCount >= 3 ) {
        this.tableData.headersCount--;
        this.tableData.headers.splice(index, 1);
        for ( let i = 0; i < this.tableData.rowsCount; i++ ) {
          this.tableData.cellsData[i].splice(index, 1);
        }
      }
    },
    addRow() {
      this.tableData.headers.forEach((element) => {
        this.newRow.push("Cell");
      });
      this.tableData.cellsData.push(
        this.newRow
      );
      this.newRow = [];
      this.tableData.rowsCount++;
    },
    removeRow(index) {
      if ( this.tableData.rowsCount >= 2 ) {
        this.tableData.cellsData.splice(index, 1);
        this.tableData.rowsCount--;
      }
    },
  },
};
</script>
<style>
</style>