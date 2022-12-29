<script>
import "vue-good-table-next/dist/vue-good-table-next.css";
import { VueGoodTable } from "vue-good-table-next";
import axios from "axios";

// add to component

export default {
  name: "my-component",
  components: {
    VueGoodTable,
  },

  data() {
    return {
      url: "http://www.omdbapi.com/?apikey=c5b429de&type=movie&s=comedy",

      columns: [
        {
          label: "Film Adı",
          field: "Title",
        },
        {
          label: "Tarihi",
          field: "Year",
        },
        {
          label: "IMDB ID",
          field: "imdbID",
        },
      ],
      rows: [],
    };
  },
  created() {
    axios.post(this.url).then((response) => (this.rows = response.data.Search));
  },
};
</script>

<template>
  <div>
    <vue-good-table
      :columns="columns"
      :rows="rows"
      :search-options="{
        enabled: true,
        trigger: 'enter',
      }"
      :pagination-options="{
        enabled: true,
        mode: 'records',
        perPage: 5,
        position: 'top',
        perPageDropdown: [3, 7, 10],
        dropdownAllowAll: false,
        setCurrentPage: 2,
        nextLabel: 'next',
        prevLabel: 'prev',
        rowsPerPageLabel: 'Rows per page',
        ofLabel: 'of',
        pageLabel: 'page', // for 'pages' mode
        allLabel: 'All',
        infoFn: (params) => `my own page ${params.firstRecordOnPage}`,
      }"
    />
  </div>
</template>
