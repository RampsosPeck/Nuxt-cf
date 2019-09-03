<template lang="html" >
	<div class="container">
		<header>
			<h1 class="title" >Álbums de la página</h1>
			<a href="https://codigofacilito.com/cursos/taller-nuxt-vue">Document</a> 
		</header>
		<div class="columns is-multiline">
			
			<AlbumCard :album="album"  v-for="album in albums" :key="album.id" />

		</div>
	</div>
</template>

<script>
	import axios from 'axios';
	import env from '../config/env';
	import AlbumCard from '../components/AlbumCard';
	export default{
	
		name: 'IndexPage',
		components: {
			AlbumCard
		},
		
		data(){
			return {
				albums: []
			}
		},

		created: async function(){
			/*axios.get(`${env.endpoint}/albums`).then(res => {
				//console.log(res.data);
				this.albums = res.data;
			});*/

			let res = await axios.get(`${env.endpoint}/albums`);
			this.albums = res.data;

		}
	
	}

</script>

<style scoped>
	
</style>


