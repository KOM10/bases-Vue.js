<script setup>
//reactividad que se refresque un elemento sin refrescar toda la pag
import {ref} from 'vue';
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
// const nombre = "yunier"
// const nombref = ()=>{
//   let number = 0
//   let dato = 7
//   return number + dato
// } //se imprime todo el objecto al solo poner el nombre de la funciiion - pero al adicionarle el () ya si retorna lo que se esta haciendo en la funcion

//variable valor true o false, esa variable en caso verda traera una variable y si es falsa se trae la de falso
// const bool = false

//for para recorrer objecto
// const data = {
//   nombre:"rosa",
//   edad:18,
//   apellido:"lopez"
// }

//:
// const color="titulo"
// con operador ternario
//const dato = false

//sin operador ternario-prueba mia
// const mia = (dat)=>{
//   if(dat === true){
//     return "true"
//   }else{
//     return "false"
//   }
// }

//reactividad que se refresque un elemento sin refrescar toda la pag
//import {ref} from 'vue'; --para que el dato pueda ser reactivo
// let dato = ref(0)

// const suma = (dato)=>dato++
// const suma = ()=>{  //las funciones flechas en una sola linea no necesita de llaves en varias lineas si las necesita
//   return dato.value++ //lo agrega en un objecto dinamico por eso necesitamos el .value
//   console.log(dato)
// }

//actividad vue clase-1 --un boton de suma que sume boton resta que reste , boton restablecer que resetee, y decimos que cuando los numero sean negativos, 
//van a ser rojos y cuando sean positivos verdes, otro boton agregar que no hace nada solo lo pondremos de momento.

let num = ref(0)

const suma =()=> num.value++

const resta =()=> num.value--

const reset =()=> num.value=0

const color = (num)=>{
  if(num>0){
    return "positivo"
  }else if(num<0){
    return "negativo"
  }
}

let numfav = ref([])
let historial = []

const agregar =()=>{ //lo estaba haciendo bien pero yo lo tenia recibiendo un parametro
  numfav.value.push(num.value)
}

const repeticion = ()=>{
  if(numfav.value.find(n=>n===(num.value))){
    return true
  }
  return false
}

</script>

<template> <!--template recive html y un poco de js relacionada al frontend-->
  <!-- <h1>hola clase {{ nombre }}</h1> -->
  <!-- <h2 v-if="nombre()>20">esto es correcto</h2> -- condicional if se muestra la etiqueta si se cumple la condicion  -->

  <!-- variable valor true o false, esa variable en caso verda traera una variable y si es falsa se trae la de falso -->
  <!-- <h2 v-if="bool===true"> el datos es verdadero : {{ bool }}</h2>
  <h2 v-else="bool===false" >el datos es falso : {{ bool }}</h2> -->

  <!--for para recorrer objecto-->
  <!-- <ul v-for="item in data" >
    <li>{{ item }}</li>
  </ul>

  <ul v-for="item, v in data" >
    <li>{{ v }}</li>
  </ul>

  <ul v-for="item, v, index in data" >
    <li>{{ index }}</li>
  </ul>

  <ul v-for="item, v, index in data" >
    <li>{{ index }} : {{ v }} : {{ item }}</li>
  </ul> -->

  <!--template: podemos poner otro template dentro de este, para poder utilizar estas operaciones sin necesidad de utilizar etiquetas del html-->
  <!-- <template v-for="item, v, index in data :key='index'" > -- identificar de lo que estamos recorriendo la clase(key), no podemos utlizar comillas dobles dentro de dobles
  </template> -->

  <!--:-->
    <!-- <h2 :class="color" >titulo</h2> -->

  <!--con operador tenrario-->
    <!-- <h2 :class="dato===true?'true':'false'">con operador ternario</h2> -->

  <!--prueba mia-->
  <!-- <h2 :class="mia(true)" >mia</h2> -->

  <!--reactividad-->
  <!-- <h1>{{ dato }}</h1>
  <button @click="suma()">+</button> -->

  <!--actividad-->
  <h1 :class="color(num)" >{{ num }}</h1>
  <button @click="suma()">+</button>
  <button @click="resta()">-</button>
  <button @click="reset()">reset</button>
  <button @click="agregar()" :disabled="repeticion()">agregar</button>
  <ul v-for="item in numfav">
    <li>{{ item }}</li>
  </ul>

  <!--comandos que traia por defecto-->
  <!-- <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main> -->
</template>

<style scoped>
/*: */
/* .titulo{
  color: rebeccapurple;
} */

/* con operador ternario */
/* .true{
  color: blue;
}
.false{
  color: red;
} */

/* actividad */

.positivo{
  color: green;
}

.negativo{
  color: red;
}

/* estilos por defecto que venian */
/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
