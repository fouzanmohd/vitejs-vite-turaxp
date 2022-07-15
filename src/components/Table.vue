<script setup lang="ts">
import { ref } from 'vue';
import { contributors } from '../data/contributors';

//getting json data
const data = contributors;

//total count of result
const totalCount = ref(data.total);

//table titles
const titles = ['Author', 'Total Contribution', 'First', 'Last', 'Clans'];

//function to format date to DD/MM/YYYY format
const formatDate = (date: Date): string => date.toLocaleDateString();

//function to format list to string
const formatListToString = (data: Array<any>): string => data.toString();
</script>

<template>
  <h4>{{ totalCount }} result(s) loaded</h4>
  <table>
    <tr>
      <th v-for="title in titles" :key="title">{{ title }}</th>
    </tr>
    <tr v-for="(data, index) in data.items" :key="index">
      <td>{{ data.author }}{{ data.author }}</td>
      <td>{{ data.total_contributions }}</td>
      <td>{{ formatDate(data.contribution_range.start) }}</td>
      <td>{{ formatDate(data.contribution_range.end) }}</td>
      <td>{{ formatListToString(data.clans_contributed_to) }}</td>
    </tr>
  </table>
</template>

<style scoped>
table {
  border: 2px solid;
}
th,
td {
  border: 1px solid;
}
</style>
