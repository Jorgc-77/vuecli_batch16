<template>
  <div>
    <h2 class="text-danger">Homework Component</h2>
    
    <div class="container">
		<div class="row">
			<div class="card-deck text-center col-md-4 mt-5" v-for="(data,i) in info" :key="i">
				<div class="card">
					<img :src="data.item_photo" class="card-img-top" alt="..." height="300">
					<div class="card-body">
						<h5 class="card-title">{{data.item_name}}</h5><br>
						<span>{{data.item_codeno}}</span>
						<p class="card-text">{{data.item_price}}</p>
						<a href="#"><i class="icofont-eye"></i></a>
						<p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
					</div>
				</div>
			</div>
		</div>
	</div>
      
        

  </div>
</template>

<script type="text/javascript">
  export default {
    name: 'Homework',
    data(){
      return {
        loading: true,
        error: false,
        info: null
      }
    },
    mounted(){
      this.getData();
    },
    methods:{
      getData(){
        this.$http.get('http://localhost:8000/api/items')
                .then(res=>{
                  console.log(res);
                  this.info = res.data.data;
                })
                .catch(err=>{
                  this.error = true;
                  console.log(err);
                })
                .finally(()=>{
                  this.loading = false;
                })
      }
    }
  }
</script>

<style type="text/css">
  
</style>