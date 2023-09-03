<script setup lang="ts">
import "ag-grid-community/styles/ag-grid.css";
import "ag-grid-community/styles/ag-theme-alpine.css";
import { AgGridVue } from "ag-grid-vue3";
import { ref } from 'vue'

const users = ref([]);
const columns = [
    {
        field: "id",
    },
    {
        field: "first_name",
    },
    {
        field: "last_name",
    },
    {
        field: "email",
    },
];


fetch('http://localhost:3000/users')
    .then(response => response.json())
    .then(data => users.value = data);
</script>

<template>
    <ag-grid-vue
        v-if="users.length"
        class="ag-theme-alpine-dark"
        style="height: 200px"
        :rowData="users"
        :columnDefs="columns"
    >
    </ag-grid-vue>
</template>
