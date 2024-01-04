<script>
import axios from 'axios'
export default{
  data(){
    return{
      pokemons: [],
      limit: 0,
      startpoint: 0
    }
  },
  methods:{
    fetchPoke(){
      axios.get(`https://pokeapi.co/api/v2/pokemon?limit=${this.limit}&offset=${this.startpoint}`)
      .then((res)=>{
        this.pokemons = res.data.results
        console.log(res.data.results)
      }
      )
    }
  },

}

</script>

<template>
<div class="container">
  <label for="limit">
    number of pokemons
  </label>
  <input  @keyup.enter="fetchPoke()" type="text" name="limit" id="limit" v-model="limit">
  <label for="startpoint">
    start point
  </label>
  <input @keyup.enter="fetchPoke()" type="text" name="startpoint" id="startpoint" v-model="startpoint">
  <button @click="fetchPoke()">show</button>
  <ul>
    <li v-for="pokemon in pokemons">{{ pokemon.name }}</li>
  </ul>
</div>
</template>

<style scoped>

</style>
