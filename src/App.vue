<script setup>

import navbarVue from './components/navbar.vue';


const carrinhos = ref({
  items: [],
  total: 0
})

function incrementar(index, lista) {
  if (lista === 1) {
    listaCompras1.value[index].quantidade++
  } else {
    listaCompras2.value[index].quantidade++
  }
}
function decrementar(index, lista) {
  if (lista === 1) {
    if (listaCompras1.value[index].quantidade > 0) {
      listaCompras1.value[index].quantidade--
    }
  } else {
    if (listaCompras2.value[index].quantidade > 0) {
      listaCompras2.value[index].quantidade--
    }
  }
}

function adicionar(index, lista) {
  if (lista === 1) {
    if (listaCompras1.value[index].quantidade > 0) {
      carrinhos.value.items.push({
        ...listaCompras1.value[index],
        preco: listaCompras1.value[index].quantidade * listaCompras1.value[index].preco
      })

      carrinhos.value.total =
        carrinhos.value.total +
        listaCompras1.value[index].preco * listaCompras1.value[index].quantidade
    }
  } else {
    if (listaCompras2.value[index].quantidade > 0) {
      carrinhos.value.items.push({
        ...listaCompras2.value[index],
        preco: listaCompras2.value[index].quantidade * listaCompras2.value[index].preco
      })

      carrinhos.value.total =
        carrinhos.value.total +
        listaCompras2.value[index].preco * listaCompras2.value[index].quantidade
    }
  }
}

function remover(index){
  const item = carrinhos.value.items.findIndex(items => items > index);
  carrinhos.value.items.splice(item, 1);
  
  
}
</script>

<template>
  
<navbar-vue></navbar-vue>

<div class="box">
    <div class="item" v-for="(item, index) in listaCompras1" :key="item.id">
      <p>Item: {{ item.nome }}</p>
      <p>Preco: {{ item.preco }}</p>
      <p>ID: {{ item.id }}</p>
      <p>quantidade: {{ item.quantidade }}</p>

      <img :src="item.img" />

      <div class="botao">
        <button class="btn btn-outline-secondary" @click="decrementar(index, 1)">-</button>
        <button class="btn btn-outline-secondary" @click="incrementar(index, 1)">+</button> <br />
        <button class="btn btn-outline-secondary" @click="adicionar(index, 1)" >Adicionar</button>
        
        
      </div>
    </div>
  </div>

</template>

<style scoped>

  
</style>
