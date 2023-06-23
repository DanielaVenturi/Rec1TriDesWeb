<script setup>
import MButton  from './components/MButton.vue'
import { ref } from 'vue'
import navbarVue from './components/navbar.vue';
const mostrar = ref(false)
const listaCompras1 = ref([
  {
    id: 1,
    nome: 'Chaveiro do Cascão-Turma Da Mônica',
    preco: 7.9,
    quantidade: 0,
    img: `https://http2.mlstatic.com/D_NQ_NP_782075-MLB41375108462_042020-O.jpg`
  },
  {
    id: 2,
    nome: 'Chaveiro do Cebolinha-Turma Da Mônica',
    preco: 7.9,
    quantidade: 0,
    img: 'https://www.lojapassatempo.com.br/galeria/produtos/gra/1201_chaveiro-de-metal-turma-da-monica-cebolinha_1966848972.jpg'
  },
  {
    id: 3,
    nome: 'Chaveiro da Magali-Turma Da Mônica',
    preco: 8.9,
    quantidade: 0,
    img: 'https://a-static.mlcdn.com.br/800x560/chaveiro-de-metal-magali-5cm-turma-da-monica-tasco/livepointgames/14983346124/2c5961e188096579a512ca563a6c3041.jpg'
  },
  {
    id: 4,
    nome: 'Chaveiro da Mônica-Turma da Mônica',
    preco: 8.9,
    quantidade: 0,
    img: 'https://lojaminasdepresentes.com.br/media/catalog/product/cache/1/thumbnail/1200x1400/9df78eab33525d08d6e5fb8d27136e95/m/d/mdy839a-m1_2_.jpg'
  },
  {
    id: 5,
    nome: 'Chaveiro do Mingau-Turma da Mônica',
    preco: 7.9,
    quantidade: 0,
    img: 'https://a-static.mlcdn.com.br/1500x1500/chaveiro-de-metal-turma-da-monica-mingau-sentado-tasco-import/livepointgames/7442083215/5c7308998df791b5da4168afe98f618f.jpg'
  },
  {
    id: 6,
    nome: 'Chaveiro do Tasco-Turma Da Mônica',
    preco: 7.9,
    quantidade: 0,
    img: 'https://imgs.casasbahia.com.br/1509127813/1xg.jpg?imwidth=500'
  }
])

const listaCompras2 = ref([
  {
    id: 1,
    nome: 'Chaveiro Elsa-Frozen',
    preco: 9.9,
    quantidade: 0,
    img: `https://atacadominasdepresentes.com.br/media/catalog/product/cache/1/thumbnail/1200x1400/9df78eab33525d08d6e5fb8d27136e95/f/z/fz-dy839a-1-d.jpg`
  },
  {
    id: 2,
    nome: 'Chaveiro coraçao irmãs de arendel-Frozen',
    preco: 11.9,
    quantidade: 0,
    img: 'https://nudelmania.vteximg.com.br/arquivos/ids/184996-1000-1000/Chaveiro-Frozen-Disney---Espuma---unidade.jpg?v=637435848667170000'
  },
  {
    id: 3,
    nome: 'Chaveiro do Olaf-Frozen',
    preco: 7.9,
    quantidade: 0,
    img: 'https://www.merchandisingplaza.com.br/228858/2/Chaveiros-Frozen-Chaveiro-Frozen-228858-l.jpg'
  },
  {
    id: 4,
    nome: 'Chaveiro BFF-Frozen',
    preco: 11.9,
    quantidade: 0,
    img: 'https://lojaminasdepresentes.com.br/media/catalog/product/cache/1/thumbnail/1200x1400/9df78eab33525d08d6e5fb8d27136e95/f/z/fz-dy839a-5-d_3_.jpg'
  },
  {
    id: 5,
    nome: 'Chaveiro da Ana-Frozen',
    preco: 7.9,
    quantidade: 0,
    img: 'https://atacadominasdepresentes.com.br/media/catalog/product/cache/1/thumbnail/1200x1400/9df78eab33525d08d6e5fb8d27136e95/f/z/fz-dy839a-2-d.jpg'
  },
  {
    id: 6,
    nome: 'Chaveiro Personalizado Elsa-Frozen',
    preco: 23.9,
    quantidade: 0,
    img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS18_WEd3DeNwR9WLfMjStyeKBS1XW0CqBpCQ&usqp=CAU'
  }
])

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

  <hr>

<h1>TURMA DA MÔNICA</h1>
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
<h1>FROZEN</h1>
  <div class="box">
    <div class="item" v-for="(item, index) in listaCompras2" :key="item.id">
      <p>Item: {{ item.nome }}</p>
      <p>Preco: {{ item.preco }}</p>
      <p>ID: {{ item.id }}</p>
      <p>quantidade: {{ item.quantidade }}</p>

      <img :src="item.img" />

      <div class="botao">
        <button class="btn btn-outline-secondary" @click="decrementar(index, 2)">-</button>
        <button class="btn btn-outline-secondary" @click="incrementar(index, 2)">+</button> <br />
        <button class="btn btn-outline-secondary" @click="adicionar(index,2 )">Adicionar</button>
      </div>
    </div>
   
  </div>
  
  

  
</template>

<style scoped>
img {
  border-style: groove;
  width: 100px;
  text-align: center;
  margin-left: 120px;
  margin-right: 75px;
}
</style>