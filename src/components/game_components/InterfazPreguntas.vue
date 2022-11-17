<script>
    import Opciones from './Opciones.vue'
    import Pregunta from './Pregunta.vue'
    import Puntajes from './Puntajes.vue'
    import Tiempo from './Tiempo.vue'

    export default{
        components: {
            Opciones,
            Pregunta,
            Puntajes,
            Tiempo
        },
        data(){
            return{
                estadoTemporizador: 'preparado',
                preguntaActiva: 0,
                turno: 0,
                respuesta: '',
                pregunta: '',
                correcto: false,
                respondido: false,
                tipoPregunta: 'normal',
                incorrectosSeguidos: 0
            }
        },
        props: ['preguntas','equipos','puntajes','puntajesDificultad','sumarPuntos','terminarJuego'],
        methods: {
            subirRespuesta(respuestaSeleccionada){
                let dificultad = this.preguntas[this.preguntaActiva].dificultad
                let puntos = dificultad === 'Difícil' ? 100 : 
                             dificultad === 'Media' ? 50 : 25
                let pregunta = this.preguntas[this.preguntaActiva]
                let audioCorrecto = new Audio('../src/assets/correcto.mp3')
                let audioIncorrecto = new Audio('../src/assets/incorrecto.mp3')

                this.respuesta =    pregunta.respuesta == 1? pregunta.opciones.opcion1 :
                                    pregunta.respuesta == 2? pregunta.opciones.opcion2 : 
                                    pregunta.respuesta == 3? pregunta.opciones.opcion3 : 
                                    pregunta.opciones.opcion4

                this.pregunta = this.preguntas[this.preguntaActiva].preguntaTexto

                if(this.tipoPregunta == 'roboPuntos'){
                    if(this.preguntas[this.preguntaActiva].respuesta == respuestaSeleccionada){
                        audioCorrecto.play()
                        this.sumarPuntos(this.turno,puntos)
                        this.correcto = true
                        this.tipoPregunta = 'normal'
                        this.preguntaActiva++
                    }
                    else{
                        audioIncorrecto.play()
                        this.correcto = false
                        this.tipoPregunta = 'preguntaPublico'
                    }
                }
                else if(this.tipoPregunta == 'normal'){
                    if(this.preguntas[this.preguntaActiva].respuesta == respuestaSeleccionada){
                        audioCorrecto.play()
                        this.sumarPuntos(this.turno,puntos)
                        this.correcto = true
                        this.preguntaActiva++
                    }
                    else{
                        audioIncorrecto.play()
                        this.tipoPregunta = 'roboPuntos'
                        this.correcto = false
                    }

                    this.turno = (this.turno + 1) % 2
                }
                else if(this.tipoPregunta == 'preguntaPublico'){
                    if(this.preguntas[this.preguntaActiva].respuesta == respuestaSeleccionada){
                        audioCorrecto.play()
                        this.correcto = true
                        this.preguntaActiva++
                        this.tipoPregunta = 'normal'
                    }
                    else{
                        audioIncorrecto.play()
                        this.correcto = false
                    }
                }

                this.respondido = true
            },
            siguientePregunta(){
                if(this.preguntaActiva === this.preguntas.length){
                    this.terminarJuego()
                }
                this.respondido = false
            }
        }
    }
</script>

<template>
    <div v-if="!this.respondido" class="interfazPregunta">
        <Puntajes :turno="this.turno" :puntajes="puntajes" :equipos="equipos" />
        <div class="int-preg-mid">
            <Pregunta :preguntaActiva="this.preguntaActiva" :preguntas="preguntas" />
            <Tiempo :preguntas="preguntas" :preguntaActiva="this.preguntaActiva" :estadoTemporizador="this.estadoTemporizador"/>
        </div>
        <Opciones :subirRespuesta="this.subirRespuesta" :opciones="preguntas[preguntaActiva].opciones" :preguntaActiva="this.preguntaActiva" />
    </div>
    <div v-if="this.respondido" class="respuesta">
        <div @click="this.siguientePregunta" v-if="this.correcto === true" class="correcto card">
            <h1>Respuesta correcta</h1>
            <p>Pregunta: <span>{{this.pregunta}}</span></p>
            <br>
            <p>Respuesta: <span>{{this.respuesta}}</span></p>
        </div>
        <div @click="this.siguientePregunta" v-if="this.correcto === false" class="card incorrecto">Respuesta incorrecta</div>
    </div>
</template>