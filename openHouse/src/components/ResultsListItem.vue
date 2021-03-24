<template>
  <div class="results-list--item">
      <div><div class="result-image">oh.</div></div>
      <div class="result-text">
        <a>{{item.formattedUrl}}</a>
        <h4 class="margin-0">{{item.title}}</h4>
        <p class="margin-0">{{item.snippet}}</p>
      </div>
    </div>
</template>

<script>

export default {
  name: 'results-list-item',
   props: {
    item: { 
      type: Object,
      default: () => {}
    }
  },
  data(){
    return {
    }
  },
  methods:{
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.margin-0{
  margin: 0;
}
.results-list--item{
  display: flex;
  margin-bottom:2rem;
}
.result-image{
  font-size: 1.8rem;
  padding: 0.5rem 0.3rem;
  background-color: #f15b33;
  color: #fff;
  font-weight: 500;
  border-radius: 0.5rem;
  width: 3rem;
  text-align: center;
}
.result-text{
  margin-left: 2rem;
}
  
  
</style>
