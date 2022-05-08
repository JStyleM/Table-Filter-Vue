<template>
  <div class="p-10">
    <div>
      <input 
        type="text"
        class="border-2 mb-5 rounded h-10 p-2"
        placeholder="Search Records"
        @input="onSearch"
      />
    </div>
    <table class="table-auto">
      <thead>
        <tr>
          <th 
            v-for="(column, index) in columns"
            v-bind:key="index"
            class="border-2 p-2 text-left"
          >
            {{ column }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(row, index) in rows"
          v-bind:key="index"
        >
          <td
            v-for="(rowItem, indexItem) in row"
            v-bind:key="indexItem"
            class="border-2 p-2 "
          >
            {{ rowItem }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

export default {
  name: 'Table',
  data () {
    return {

      rawRows: [
        ['Jhonatan','32','Software Develop','1989'],
        ['Marcos','23','Doctor','1996'],
        ['Pablo','36','Teacher','1985'],
        ['Miguel','45','Psycology','1994'],
        ['Roberto','28','Driver','1990'],
        ['Andres','30','Sales Manager','1993'],
        ['Yordan','27','Supervisor','1995'],
      ],

      rows: [],

      columns: [
        'name',
        'Age',
        'Profession',
        'Year of Birth'

      ]
    }
  },

  methods: {

    performSearch(rows, term) {
      
      const results = rows.filter(row => row.join(' ').toLowerCase().includes(term))
      return results

    },

    onSearch (e) {

      const term = e.target.value.toLowerCase()
      this.rows = this.performSearch(this.rawRows, term)

    },

  },

  mounted () {

    this.rows = this.rawRows

  }

}
</script>