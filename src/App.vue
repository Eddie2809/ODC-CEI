<script>
  import Home from './components/Home.vue'
  import SubirPreguntas from './components/SubirPreguntas.vue'
  import Jugar from './components/Jugar.vue'
  import SeleccionEquipos from './components/SeleccionEquipos.vue'

  export default{
    components: {
      Home,
      Jugar,
      SubirPreguntas,
      SeleccionEquipos
    },
    data(){
      return{
        route: 'Home',
        equipos: [],
        ronda: 1,
        puntajesDificultad: [25,50,100],
        preguntas: []
      }
    },
    methods: {
      changeRoute(newRoute){
        this.route = newRoute
      },
      asignarPreguntasYEquipos(preguntas,equipos){
        this.preguntas = preguntas
        this.equipos = equipos
      }
    }
  }
</script>

<template>
  <div class="App">
    <Home v-if="route === 'Home'" :changeRoute = "changeRoute"/>
    <Jugar :puntajesDificultad="this.puntajesDificultad" :preguntas="this.preguntas" :equipos="this.equipos" :ronda="this.ronda" v-if="route === 'Jugar'"/>
    <SubirPreguntas v-if="route === 'SubirPreguntas'"/>
    <SeleccionEquipos :asignarPreguntasYEquipos="this.asignarPreguntasYEquipos" :changeRoute="changeRoute" v-if="route === 'seleccionEquipos'"/>
  </div>
 </template>