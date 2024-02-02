<template>
    
    <div class="overflow-auto">
        <b-container>
      <b-breadcrumb :items="items"></b-breadcrumb>
    </b-container>
      <b-pagination
        v-model="currentPage"
        :total-rows="rows"
        :per-page="perPage"
        aria-controls="my-table"
      ></b-pagination>
  
      <p class="mt-3">Current Page: {{ currentPage }}</p>
  
      <b-table
        id="my-table"
        :items="items"
        :per-page="perPage"
        :current-page="currentPage"
        small
      ></b-table>
    </div>
  </template>
  
  <script>
    export default {
      data() {
        return {
          perPage: 3,
          currentPage: 1,
          items: [
           
            {
          text: "Inicio",
          to: { name: "inicio" },
        },
        {
          text: "Paginacion",
          active: true,
        },
          ]
        }
      },
      computed: {
        rows() {
          return this.items.length
        }
      },
      
    }
  </script>