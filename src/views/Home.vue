<template>
  <div class="container my-5">
    <user-search-form @clicked="queryEvent"></user-search-form>
    <!-- <b-table :data="users" :columns="columns"></b-table> -->
    <b-table
      :data="filterMembers"
      :paginated="isPaginated"
      :per-page="perPage"
      :current-page.sync="currentPage"
      :pagination-simple="isPaginationSimple"
      :pagination-position="paginationPosition"
      :default-sort-direction="defaultSortDirection"
      :pagination-rounded="isPaginationRounded"
      :sort-icon="sortIcon"
      :sort-icon-size="sortIconSize"
      default-sort="name"
      aria-next-label="Next page"
      aria-previous-label="Previous page"
      aria-page-label="Page"
      aria-current-label="Current page"
    >
      <b-table-column field="name" label="Name" sortable v-slot="props">
        {{ props.row.name }}
      </b-table-column>

      <b-table-column field="age" label="Age" sortable v-slot="props">
        {{ props.row.age }}
      </b-table-column>

      <b-table-column field="sex" label="Sex" sortable centered v-slot="props">
        {{ props.row.sex }}
      </b-table-column>
      ></b-table
    >
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import titanic from "../assets/titanic.json";
import UserSearchForm from "@/components/parts/UserSearchForm.vue";

let userArray: any[] = [];

export default Vue.extend({
  components: { UserSearchForm },
  name: "Home",
  data() {
    return {
      searchValue: "",
      isPaginated: true,
      isPaginationSimple: false,
      isPaginationRounded: false,
      paginationPosition: "bottom",
      defaultSortDirection: "asc",
      sortIcon: "arrow-up",
      sortIconSize: "is-small",
      currentPage: 1,
      perPage: 5,
      prevIcon: "chevron-left",
      nextIcon: "chevron-right",
      users: titanic,
      buttonName: "",
      searchQuery: null,
      columns: [
        {
          field: "name",
          label: "Name"
        },
        {
          field: "sex",
          label: "Sex"
        },
        {
          field: "age",
          label: "Age"
        }
      ]
    };
  },

  computed: {
    filterMembers: function() {
      let filtered = userArray;
      if (this.searchValue) {
        filtered = userArray.filter(
          m => m.name.toLowerCase().indexOf(this.searchValue) > -1
        );
      }

      return filtered;
    }
  },
  methods: {
    queryEvent: function(value: string) {
      this.searchValue = value;
    },
  },
  created() {
    userArray = titanic;
  },
});
</script>
