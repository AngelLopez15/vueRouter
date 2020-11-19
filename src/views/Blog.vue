<template>
  <Titulo texto="Hola Vue Router. Este es el Blog" />

  <!-- Boton para consumir API -->
  <!-- <button @click="consumirAPI">Consumir API</button> -->
  
  <!-- Para convertir cada uno de nuestros titulos en un link que nos lleve
  al contenido de na nota del blog -->
  <p v-for="item in arrayBlog" :key="item.id">
    <!-- Debemos poner la ruta de los articulos que configuramos en el router pero
    remplazando el id estatico por una variable de javascript -->
    <router-link :to="`/blog/${item.id}`">
      {{item.title}}
    </router-link>  
  </p>


</template>

<script>
import Titulo from '../components/Titulo'
export default {
  components:{
    Titulo
  },
  data(){
    return{
      arrayBlog:[]
    }
  },
  methods:{
    // Como vamos a consumir una API y hacer una solicitus vamos a trabajar con asyn await
    async consumirAPI(){
      try {
        // estamos haciendo la peticion a la API
        const data = await fetch('https://jsonplaceholder.typicode.com/posts')
        // guardando los datos obtenidos en un arreglo
        const array = await data.json()
        // console.log(array)
        this.arrayBlog=array
      } catch (error) {
        console.log(error)
      }
    }
  },
  // El ciclo de vida de create nos sirve (entre muchas) en este caso para
  // hacer el llamado a la API sin necesidad de estar cargando apretando el boton
  // Asi al entrar a la pagina ya se abra ejecutado y renderizado en pantalla por que en el 
  // ciclo de vida de create este ya tiene todos los que hay en la seccion de scripts 
  created(){
    this.consumirAPI()
  }
}
</script>

<style>

</style>