<template>
  <Titulo texto="Esta es una Ruta con parametros" />
  <!-- Para acceder y renderizar al parametro de la url 
  al que estamos accediendo usamos $route.params.id
  En este caso es "id" por que asi lo declaramos en el route -->
  <h2>Parámetro: {{$route.params.id}}</h2>
  <h3>{{articulo.title}}</h3>
  <p>{{articulo.id}} - {{articulo.body}}</p>
</template>

<script>
import Titulo from '../components/Titulo'
export default {
  components:{
    Titulo
  },
  data(){
    return{
      // Es un objeto por que los articulos de la API vienen en forma de objeto JSON
      articulo:{}
    }
  },
  methods:{
    async consumirArticulo(){
      try {
        const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
        const objeto = await data.json()
        // guardando los datos traidos en "articulo"
        this.articulo = objeto
      } catch (error) {
        console.log(error)
      }
    }
  },
  created(){
    this.consumirArticulo()
  }
}
</script>

<style>

</style>