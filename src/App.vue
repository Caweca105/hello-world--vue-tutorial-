<template>
  <HelloWorld :name="name" @pressed="pressed" />
  <div v-if="pokemon">
    <img :src="pokemon.sprites.back_default" alt="" />
  </div>
</template>

<script lang="ts" setup>
//this import is highlighted in red and I don't know why, it works though
  import HelloWorld from "./components/HelloWorld.vue";
  import { ref } from "vue";
  let name = "Diogo";
  let pokemon = ref(null) as any;

  async function pressed() {
    const info = await fetch("https://pokeapi.co/api/v2/pokemon/ditto");
    const json = await info.json();
    pokemon.value = json;
    console.log(pokemon.value);
  }
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
