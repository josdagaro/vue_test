<template>
  <div class="table-responsive">
    <div class="section">
      <div class="col-md-6 col-md-offset-3">
        <div class="form-group">
          <label for="query">Search</label>
          <input v-model="searchQuery" type="text" class="form-control" id="query" placeholder="Enter your query">
        </div>
      </div>
    </div>
    <table class="table table-striped">
      <thead>
        <th v-for="key in columns"
          @click="sortBy(key)"
          :class="{ active: sortKey == key }" :key="key"
          class="text-center">
          {{ key | capitalize }}
          <span class="glyphicon" :class="sortOrders[key] > 0 ? 'glyphicon-chevron-up' : 'glyphicon-chevron-down'"></span>
        </th>
      </thead>
      <tbody>
        <tr v-for="entry in filteredData" :key="entry.id">
          <td v-for="key in columns" :key="key">{{entry[key]}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

export default {
  name: 'HotelsGrid',
  props: {
    data: Array,
    columns: Array,
  },
  data(){
    return {
      searchQuery: '',
      sortKey: '',
      sortOrders: {},
    }
  },
  computed: {
    filteredData: function () {
      let sortKey = this.sortKey;
      let filterKey = this.searchQuery && this.searchQuery.toLowerCase();
      let order = this.sortOrders[sortKey] || 1;
      let data = this.data;

      if (filterKey) {
        data = data.filter(function (row) {
          return Object.keys(row).some(function (key) {
            return String(row[key]).toLowerCase().indexOf(filterKey) > -1;
          })
        })
      }
      if (sortKey) {
        data = data.slice().sort(function (a, b) {
          a = a[sortKey];
          b = b[sortKey];
          return (a === b ? 0 : a > b ? 1 : -1) * order;
        })
      }
    return data;
    },
  },
  filters: {
    capitalize: function (str) {
      return str.charAt(0).toUpperCase() + str.slice(1);
    }
  },
  methods: {
    sortBy: function (key) {
      this.sortKey = key;
      this.sortOrders[key] = this.sortOrders[key] * -1
    },
  },
  created(){
    let sortOrders = {};
    this.columns.forEach(function (key) {
      sortOrders[key] = 1;
    })
    this.sortOrders = sortOrders;
  }
}
</script>
