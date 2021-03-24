<template>
  <div clas="main">
    <div id="app">
      <search-header @search="searchDebounce"></search-header>
      <results-list v-if="results.items && results.items.length && !loading" :data="results.items"></results-list>
      <div class="center-text" v-else-if="loading">loading...</div>
      <div class="center-text" v-else>{{ errorText || `No Data Available!!` }}</div>
    </div>
    <pagination v-if="results.searchInformation && results.searchInformation.totalResults > 0" :pages="results.searchInformation && results.searchInformation.totalResults ? Math.floor(results.searchInformation.totalResults/10) +1  : 0" @pageSwitch="getNextResults"></pagination>
  </div>
</template>

<script>
import axios from "axios"
import _ from "lodash"
import SearchHeader from './components/SearchHeader.vue'
import ResultsList from './components/ResultsList.vue'
import Pagination from './components/Pagination.vue'

export default {
  name: 'App',
  components: {
    SearchHeader,
    ResultsList,
    Pagination
  },
  data(){
    return {
      results: {},
      loading: false,
      errorText: null
    }
  },
  computed: {
    key(){
      return "AIzaSyDeq72CZovX3DnDbYXo1qNxT7i2m2MFiWw"
    },
    engineId() {
      return "73513ada48a4e8411"
    }
  },
  methods:{
    renderList(list){
      this.results = list;
    },
    searchDebounce: _.debounce(function(query){
      this.search(query);
    }, 300),
    search(query, page=0){
      this.loading = true;
      this.query = query;
      axios.get(`https://www.googleapis.com/customsearch/v1?key=${this.key}&cx=${this.engineId}&q=${query}&start=${page*10+1}`).then(response => { 
        this.results = response.data;
        this.loading = false;
        this.errorText = null;
      })
      .catch(() => {
        this.loading= false;
        this.errorText="Some went wrong, please try again later!"
      })
    },
    getNextResults(pageNo){
      this.search(this.query, pageNo);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
  /* display: flex; */
  /* justify-content: center; */
}
.center-text{
  text-align:center;
  margin-top:10rem;
}
</style>
