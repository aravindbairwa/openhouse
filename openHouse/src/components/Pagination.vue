<template>
  <div class="pagination">
    <a href="#">&laquo;</a>
    <a :class="index === activeIndex && 'active'" v-for="(page,index) in pages" :key="index" @click="$emit('pageSwitch', index); activeIndex = index">{{index+1}}</a>
    <a href="#">&raquo;</a>
  </div>
</template>

<script>
export default {
  name: 'pagination',
  props: {
    pages: {
      type: Number,
      default: () => 0
    }
  },
  data(){
    return {
      activeIndex: 0
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pagination {
  display: flex;
    text-align: center;
    justify-content: center;
}

.pagination a {
  color: black;
  float: left;
  padding: 8px 16px;
  text-decoration: none;
}

.pagination a.active {
  background-color: #f05b33;
  color: white;
  border-radius: 5px;
}

.pagination a:hover:not(.active) {
  background-color: #ddd;
  border-radius: 5px;
}
</style>
