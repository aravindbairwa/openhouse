<template>
  <div class="header-wrapper">
    <div class="logo">oh. search</div>
    <label class="search-box"><input type="text" placeholder="Search..." @keyup="$emit('search', query)" v-model="query"><button></button></label>
  </div>
</template>

<script>
export default {
  name: 'search-header',
  mounted(){
  },
  data(){
    return {
      query: ""
    }
  },
  methods:{
    
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .header-wrapper{
    display: flex;
  }
  .logo{
      font-size: 1.8rem;
      color: #f05b33;
      margin-right: 3rem;
      font-weight: 500;
  }
  .search-box{
    border: 0.1rem solid #efefef;
    padding: 0 1rem;
    border-radius: 0.5rem;
    box-shadow: 10px 10px 5px -10px rgba(51,51,51,0.75);
    -webkit-box-shadow: 10px 10px 5px -10px rgba(51,51,51,0.75);
    -moz-box-shadow: 10px 10px 5px -10px rgba(51,51,51,0.75);
  }
  .search-box input{
    border: none;
    font-size: 1.4rem;
    min-width: 30rem;
    outline: none;
    padding: 1rem;
  }
  .search-box button{
    border: none;
    background: transparent;
  }
  
</style>
