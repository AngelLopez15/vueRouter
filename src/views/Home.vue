<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <Titulo texto="Este es el Home" />
  </div>
</template>

<script>
// @ is an alias to /src
import Titulo from '@/components/Titulo'

export default {
  name: 'Home',
  components: {
    Titulo
  }
}
</script>
