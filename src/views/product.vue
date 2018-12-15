<template>
    <div>
        <h1>Product List</h1>
        <b-table striped hover :items="Products" :fields="fields" :per-page="pageSize" :current-page="pageIndex">
    </b-table>
        <b-pagination size="md" :total-rows="Products.length" v-model="pageIndex" :per-page="pageSize">
    </b-pagination>
        
    </div>    
</template>
<script>

import axios from 'axios'
export default {
  name: 'Products',
  data(){
      return{
          message:'Project 2',
          Products:[],
          pageSize :10,
          pageIndex:1,
          fields: [{
              key:'ProductID',
              sortable : true
          },
          {
              key:'ProductName',
              sortable : true
          },
          {
              key:'SupplierID',
              sortable : true,
              variant:'success'
          },
          {
              key:'CategoryID',
              sortable : true
          },
          ],
      }
  },
  mounted(){
      var instance = this
      axios
      .get('https://infinite-sea-36672.herokuapp.com/api/Products')
      .then(function(response){
          console.log(response.data)
          instance.Products =response.data.data
      })
  }
  }
</script>
