<script>
    import Bienvenida from './game_components/Bienvenida.vue'
    import InterfazPreguntas from './game_components/InterfazPreguntas.vue'
    import PresentacionEquipos from './game_components/PresentacionEquipos.vue'
    import PuntajeFinal from './game_components/PuntajeFinal.vue'

    export default{
        components: {
            Bienvenida,
            InterfazPreguntas,
            PresentacionEquipos,
            PuntajeFinal
        },
        data(){
            return{
                puntajes: [0,0],
                estadoDelJuego: "bienvenida"
            }
        },
        props: ['preguntas','equipos','ronda','puntajesDificultad'],
        methods: {
            keyEvent(){
                
            },
            sumarPuntos(equipo, puntos){
                this.puntajes[equipo] += puntos
            },
            cambiarEstado(){
                if(this.estadoDelJuego == 'bienvenida'){
                    this.estadoDelJuego = 'presentacionEquipos'
                }
                else if(this.estadoDelJuego == 'presentacionEquipos'){
                    this.estadoDelJuego = 'jugando'
                }
            },
            terminarJuego(){
                this.estadoDelJuego = 'finalizado'
            }
        }
    }
</script>

<template>
    <div class="Game" @click="this.cambiarEstado()">
        <Bienvenida v-if="estadoDelJuego === 'bienvenida'"/>
        <PresentacionEquipos :equipos="equipos" v-if="estadoDelJuego === 'presentacionEquipos'"/>
        <InterfazPreguntas :terminarJuego="this.terminarJuego" :sumarPuntos="this.sumarPuntos" :puntajesDificultad="puntajesDificultad" :puntajes="this.puntajes" :preguntas="preguntas" :equipos="equipos" v-if="estadoDelJuego === 'jugando'"/>
        <PuntajeFinal :equipos="equipos" :puntajes="this.puntajes" v-if="estadoDelJuego === 'finalizado'"/>
    </div>
</template>