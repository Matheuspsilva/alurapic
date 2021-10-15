<template>
  <div id="app">

    <h1>{{ titulo }}</h1>
    <ul>
      <li v-for="foto of fotos" v-bind:key="foto.id">
        <img :src="foto.url" :alt="foto.titulo">
      </li>
    </ul>

  </div>
</template>

<script>
export default {
  data(){
    return{
      titulo:'Alurapic',
      fotos: []

    }
  },

  created(){

    let promise = this.$http.get('http://localhost:3000/v1/fotos');

    promise
      .then(res => res.json())
      .then(resultadoJson => this.fotos = resultadoJson, err => console.log(err));

  }
}
</script>

<style>

</style>
