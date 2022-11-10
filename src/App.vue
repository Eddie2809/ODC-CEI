<script>
  import Home from './components/Home.vue'
  import SubirPreguntas from './components/SubirPreguntas.vue'
  import Jugar from './components/Jugar.vue'

  import {preguntas} from './rondas/ronda1.js'

  export default{
    components: {
      Home,
      Jugar,
      SubirPreguntas
    },
    data(){
      return{
        route: 'Home',
        equipos: ["Lechugas","Tomates"],
        ronda: 1,
        puntajesDificultad: [25,50,100],
        preguntas: preguntas
      }
    },
    methods: {
      changeRoute(newRoute){
        this.route = newRoute
      }
    }
  }
</script>

<template>
  <div class="App">
    <Home v-if="route === 'Home'" :changeRoute = "changeRoute"/>
    <Jugar :puntajesDificultad="this.puntajesDificultad" :preguntas="this.preguntas" :equipos="this.equipos" :ronda="this.ronda" v-if="route === 'Jugar'"/>
    <SubirPreguntas v-if="route === 'SubirPreguntas'"/>
  </div>
 </template>