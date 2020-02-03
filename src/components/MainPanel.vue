<template>
  <mdb-container class="main-panel">
    <h2>{{title}}</h2>
    <mdb-datatable
      :data="data"
      striped
      bordered
      responsive
      focus
      @selectRow="selectHandler"
    />
  </mdb-container>
</template>

<script>
  import { mdbContainer, mdbDatatable } from 'mdbvue';
  export default {
    name: 'MainPanel',
    components: {
      mdbContainer,
      mdbDatatable
    },
    data() {
      return {
        columns: [],
        rows: [],
        entries: []
      };
    },
    props: {
      title: String,
      url: String
    },
    computed: {
      data() {
        return {
          columns: this.columns,
          rows: this.rows,
        };
      },
    },
    methods: {
      filterData(dataArr, keys) {
        let data = dataArr.map(entry => {
          let filteredEntry = {};
          keys.forEach(key => {
            if (key in entry) {
              filteredEntry[key] = entry[key];
            }
          });
          return filteredEntry;
        });
        return data;
      },
      selectHandler(index) {
        let detail = this.entries[index]
        this.$emit("select", detail);
      }
    },
    mounted(){
      fetch(this.url)
        .then(res => res.json())
        .then(json => {
          let keys = []
          if (this.title === 'Users')
            keys = ["id", "name"];
          else if (this.title === 'Posts')
            keys = ["id", "title"];
          let entries = this.filterData(json, keys);
          //columns
          this.columns = keys.map(key => {
            return {
              label: key.toUpperCase(),
              field: key,
              sort: 'asc'
            };
          });
          //rows
          entries.map(entry => this.rows.push(entry));
          json.map(entry => this.entries.push(entry));

          this.$emit("select", this.entries[0]);
        })
        .catch(err => console.log(err));
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
