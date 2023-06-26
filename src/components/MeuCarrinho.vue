<script setup></script>
<template>
    <div class="carrinho" v-if="mostrar">
     <h1>Seu Carrinho</h1>
   
   <button class="btn btn-outline-secondary"  @click="mostrar = false">Fechar Carrinho</button>
  
   <div class="item" v-for="item in carrinhos.items" :key="item.id">
     <p>Item: {{ item.nome }}</p>
     <p>Preco: {{ item.preco.toFixed(2) }}</p>
     <p>ID: {{ item.id }}</p>
     <p>Quantidade: {{ item.quantidade }}</p>
     <img :src="item.img" />
     <div >
       <button class="btn-close" aria-label="Close" @click="remover"></button>
   </div>
 </div>
   <h1>Total:{{ carrinhos.total.toFixed(2) }}</h1>
 </div>
</template>
<style scoped>

</style>