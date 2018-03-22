<template>
	<div class="AppCEP">
		<img class="img" src="https://www.buscaeu.com.br/uploads/blog/conheca-o-cep-das-ruas-de-cianorte-470.png">
		<form>
			<label for="cep">Cep</label>
			<input type="text" name="cep" placeholder="entre com seu Cep" v-model="cep" @keyup.enter="getData()">
			<label for="street">Rua</label>
			<input type="text" name="street" placeholder="" v-model="street">
			<label for="city">Cidade</label>
			<input type="text" name="city" placeholder="" v-model="city">
			<label for="uf">UF</label>
			<input type="uf" name="uf" placeholder="" v-model="uf">
			<button>submit</button>
		</form>
	</div>
</template>
<script>
import axios from 'axios'

export default{
	name: "Cep",
	data(){
		return{
			cep:'',
			street:'',
			city:'',
			uf:'',	
		}
	},
	methods:{
		getData(){  
			axios.get('https://viacep.com.br/ws/'+this.cep+'/json/')
		    .then(response => {
				this.street = response.data.logradouro
				this.city = response.data.localidade
				this.uf = response.data.uf  
			})
		} 	
	}
}
	
</script>
<style scoped>
	.AppCEP{
		display: flex;
		align-items: center;
		justify-content: center;
		border-radius: 30%;
		background: green;
		font-size: 3vh;
		flex-wrap: wrap;
	}
	.img{
		width: 30%;
		height: 30%;
	}
</style>