<template>
  <ul class="results-list">
    <li v-for="(item ,index) in data" :key="index">
      <results-list-item :item="item"></results-list-item>
    </li>
  </ul>
</template>

<script>
import ResultsListItem from './ResultsListItem.vue'

export default {
  components: { ResultsListItem },
  name: 'results-list',
  props: {
    data: {
      type:  Array,
      default: () => []
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.results-list{
  list-style: none;
  margin-top:2rem;
}
  
</style>
