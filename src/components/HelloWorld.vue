<template>
  <div>
    {{ vmodel }}
    <vue-good-table
      :columns="columns"
      :rows="rows">
      <template slot="table-row" slot-scope="props">
        <span v-if="props.column.field == 'description'">
          <button type="button" class="btn btn-primary">
          View Details
          </button>
        </span>
        <span v-else-if="props.column.field == 'sex'">
          <input type="text" :name="'hoge' + props.column.field" v-model="rows[props.index].sex">
        </span>
      </template>
    </vue-good-table>
  </div>
</template>

<script>
export default {
  name: 'my-component',
  data(){
    return {
      columns: [
        {
          label: 'Name',
          field: 'name',
        },
        {
          label: 'Age',
          field: 'age',
          type: 'number',
        },
        {
          label: 'Description',
          field: 'description',
          html: true,
        },
        {
          label: 'Sex',
          field: 'sex',
          html: true,
        },
      ],
      vmodel: "",
      rows: [
        { id:1, name:"John", age: 20, description: '', sex: 'man' },
        { id:2, name:"Jane", age: 24, description: '', sex: 'woman' },
        { id:3, name:"Bob", age: 23, description: '', sex: 'man' },
        { id:4, name:"Mike", age: 56, description: '', sex: 'man' },
        { id:5, name:"Kathy", age: 35, description: '', sex: 'woman' },
        { id:6, name:"Tess", age: 80, description: '', sex: 'woman' },
      ],
    };
  },
};
</script>
