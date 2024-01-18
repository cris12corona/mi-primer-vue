<script setup>
import {ref ,computed} from 'vue'

const name = "Vue dinamico";
const styleColor = "color: blue;";
const arrayColores = ["blue", "red","peru"];
const activo = false;
const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];

const classCounter = computed (() => {
  if( counter.value === 0){
    return 'zero'
  }
  if( counter.value > 0){
    return 'positive'
  }
  if( counter.value < 0){
    return 'negative'
  }
})

const counter = ref(0);

const limpiar = () => {
  counter.value = 0;
}
const increment = () => {
  console.log('aumentar contador');
  counter.value ++;
  console.log(counter)
}

const desincrement = () => {
  console.log('desincrementar contador');
  counter.value --;
  console.log(counter)
}

const objfrutas = {
            id:1,          
            name: "Manzana",
            price: "$1.00",
            description: "Una manzana"
};

const arrayFrutas2 = [
        {
            id:1,          
            name: "Manzana",
            price: "$1.00",
            description: "Una manzana",
        },
        {
            id:2,
            name: "Pera",
            price: "$2.00",
            description: "Una pera",
        },
        {
            id:3,
            name: "Naranja",
            price: "$3.00",
            description: "Una naranja",
        },
    ];

    const arrayFrutas3 = [
    {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    },
    {
        name: "Pera",
        price: "$2.00",
        description: "Una pera",
        stock: 10,
    },
    {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
        stock: 20,
    },
];   
const users = [
  {
    id: 1,
    name: 'Juan',
    posts: [
      { id: 1, title: 'Mi primer post' },
      { id: 2, title: 'Mi segundo post' },
    ]
  },
  {
    id: 2,
    name: 'Maria',
    posts: [
      { id: 3, title: 'Mi tercer post' },
      { id: 4, title: 'Mi cuarto post' },
    ]
  }
]
//funcion en javascript
const handleclick = (mensaje) => {
  console.log(mensaje)
}

const arrayFavoritos = ref([])

const add = () => {
  arrayFavoritos.value.push(counter.value);

}

const bloquearBtnAdd = computed(() => {
  const numSearch = arrayFavoritos.value.find((numero) => numero 
  === counter.value);
  console.log(numSearch);
  //if(numSearch === 0 ) return true
  //return numSearch ? true : false;

  return numSearch || numSearch === 0

})




</script>

<template>

  <h1 v-bind:style="styleColor">Hola soy azul</h1><br>
  <!-- <button v-on:click="handleclick('hola mundo')">Activame</button>
  <button @click="handleclick('hola mundo 2')">Activame</button>
  <button v-on:click.right.prevent="handleclick('Texto Right')">Activame Right</button>
  <button v-on:click="handleclick('Texto left')">Activame left</button>
  <button v-on:click.middle="handleclick('Texto middle')">Activame middle</button>
   <h2>{{ activo ? "Estoy activo" : "Estoy inactivo"}}</h2> 
  <h2 v-if="activo">Estoy activo</h2>
  <h2 v-else>Estoy inactivo</h2>
  <h2 v-if="!activo">Estoy inactivo</h2>
  <h2 v-if ="activo === true">
    <span>Icono</span>
    Estoy activo
  </h2>
  <h2 v-else-if=" activo === false">Estoy inactivo</h2>
  <h2 v-else>Estoy indeciso</h2>
  <br>
  <h2 v-show="activo">Estoy activo v-show</h2><br>
  
  <ul>
    <li v-for="(fruta, h) in arrayFrutas" :key="h"
    >
    {{h}} - {{fruta }}

    </li>
  </ul>

  <ul>
    <li v-for=" (mercado,id) in arrayFrutas2" :key="id">
     {{ mercado.id }} - {{mercado.name}} - {{ mercado.price }} - {{ mercado.description }}

    </li>
  </ul>
  <ul>
    <br>
    <li v-for="(value, propiedad, posicion) in objfrutas" :key="value">
      {{ posicion }} - {{ propiedad }} : {{ value }}

    </li>
  </ul>

  

  <ul>
    <br>
    <template v-for="(fruta, id) in arrayFrutas3" :key="id">
      <li v-if="fruta.stock > 1">
        {{ fruta.name }}:{{ fruta.price }}
      </li>
    
    </template>

    

  </ul>

  <ul>
    <template>
  <div>
    <h2>Lista de usuarios:</h2>
    <ul>
      <template
        v-for="user in users"
        :key="user.id"
      >
        <li>
          <h3>{{ user.name }}</h3>
          <ul>
            <template
              v-for="post in user.posts"
              :key="post.id"
            >
              <li>{{ post.title }}</li>
            </template>
          </ul>
        </li>
      </template>
    </ul>
</div>
</template>
 
  </ul>-->
  <h2 :class="classCounter">{{counter }}</h2>
  <button @click="increment" class="btn btn-success">Aumentar</button>
  <button @click="desincrement" class="btn btn-danger">Disminuir</button>
  <button @click="limpiar" class="btn btn-secondary">limpiar</button>
  <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-primary">Add</button><br>
  {{ arrayFavoritos }}
  <ul>
    <li
      v-for="(numero, index) in arrayFavoritos" :key="index">
      {{numero }}
    </li>
  </ul>
   

</template>

<style>
h1{
  color: black;
}
.positive {
  color:green;
}
.negative {
  color:red;
}

.zero {
  color: black;
}
</style>