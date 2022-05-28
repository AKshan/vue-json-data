
<script>
export default {
    async created() {
    const baseURL = "https://swapi.dev/api/people"
    const response = await fetch(`${baseURL}`);
    const data = await response.json();
    this.res = data.results;
    // console.table(this.res)

    },
    data(){
        return{
            searchQuery: '',
            res: []
        }    
    },

    methods:{
        // Sort Names
        sortBy(prop){
            this.res.sort((a,b) => 
                (a[prop] < b[prop]) ? -1 : 1
            )
        }
    },
    computed: {
        // Filter Function
        filteredData: function() {
        return this.res.filter(item => {
            return item.name.match(this.searchQuery)
            });
        }
    }

};


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
main{
  border-radius: 3px;
}

main h1{
    color: #800080;
}

.table-layout{
    display: grid;
    gap: 20px;
    margin: 20px;
}

table{
    border: 1px solid #e0b8e0;
    border-collapse: collapse;    
    background: #f7f3f7;
}

table tr th, table tr td{
    border-bottom: 1px solid #efddef;
    padding: 6px 10px;
}

table tr th{
    border-bottom: 1px solid #e0b8e0;
    color: #800080;
    vertical-align: middle;
}

table tr td{
    background-color: #fffeff;
}

table tr:last-child td{
    border-bottom-color: #e0b8e0;
}


table tr th:first-child, table tr td:first-child{
    text-align: left;
    padding-left: 20px;
}

input, button{
    padding: 8px 10px;
    cursor: pointer;
    border: 1px solid #800080;
    border-radius: 3px;
    min-width: 200px;
}

/* arrow sort */
span.arrow-down {
  width: 0; 
  height: 0; 
  border-left: 6px solid transparent;
  border-right: 6px solid transparent;
  border-top: 6px solid #800080;
  display: inline-flex;
}

</style>

<template>
<main>
  <h1>Get API from server</h1>

<!-- Search box -->
    Search Name: 
  <input type="text" placeholder="Search" v-model="searchQuery" v-on:input="search">
  
<!-- Table Layout -->
  <div class="table-layout">
  <table>
      <tr>
          <th @click="sortBy('name')">Name <span class="arrow-down"></span></th>
          <th>Height</th>
          <th>Mass</th>
          <th>Hair Color</th>
          <th>Skin Color</th>
          <th>Eye Color</th>
          <th>Birth Year</th>
          <th>Gender</th>
      </tr>
      <tr v-for="(value, index) in filteredData" :key="index">

        <td>
            {{value.name}}
        </td>
        <td>
            {{value.height}}
        </td>
        <td>
            {{value.mass}}
        </td>
        <td>
            {{value.hair_color}}
        </td>
        <td>
            {{value.skin_color}}
        </td>
        <td>
            {{value.eye_color}}
        </td>
        <td>
            {{value.birth_year}}
        </td>
        <td>
            {{value.gender}}
        </td>
          
      </tr>
  </table>
  </div>
</main>
</template>
