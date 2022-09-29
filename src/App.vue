<template>
  <ejs-treegrid :dataSource="data"
    childMapping="subtasks"
    :treeColumnIndex="1"
    :height='400' 
    :allowFiltering="true"
    :filterSettings="filterOptions"
    :allowPaging='true' 
    :pageSettings='pageSettings'>
    <e-columns>
      <e-column field='taskID' headerText='Task ID' width='80' textAlign='Right'></e-column>
      <e-column field='taskName' headerText='Task Name' width='190'></e-column>
      <e-column field='startDate' headerText='Start Date' width='100' format="yMd" textAlign='Right'></e-column>
      <e-column field='duration' headerText='Duration' width='90' textAlign='Right'></e-column>
      <e-column field='progress' headerText='Progress' width='90' textAlign='Right'></e-column>
    </e-columns>
  </ejs-treegrid>
</template>

<script>
import { TreeGridComponent, ColumnsDirective, ColumnDirective, Page, Filter} from "@syncfusion/ej2-vue-treegrid";
import {sampleData} from './data.js';

export default{
  name: 'App',
  components: {
    'ejs-treegrid': TreeGridComponent,
    'e-columns': ColumnsDirective,
    'e-column': ColumnDirective
  },
  data: () => {
    return {
      data: sampleData,
      filterOptions: {
        ignoreAccent:true, 
        hierarchyMode:"None",
        type: "Excel",
        // Uncomment below code for initial filtering
        // columns:[{
        //   field: "taskName",
        //   matchCase: false,
        //   operator: "startswith",
        //   predicate: "and",
        //   value: "plan"
        // }]
      },
      pageSettings: { pageSize: 12 }
    }
  },
  provide:{
    treegrid:[Page, Filter]
  }
}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-treegrid/styles/material.css";
</style>
