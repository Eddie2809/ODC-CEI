<script>
    import {equipos} from '../rondas/equipos.js'
    import {preguntas1} from '../rondas/ronda1.js'
    import {preguntas2} from '../rondas/ronda2.js'
    import {preguntas3} from '../rondas/ronda3.js'

    export default{
        props: ['changeRoute','asignarPreguntasYEquipos'],
        data(){
            return{
                ronda: "1",
                equipoA: '',
                equipoB: '',
                equipos: equipos
            }
        }
    }
</script>

<template>
    <p>Selecciona el primer equipo</p>
    <select v-model="equipoB" name="" id="">
        <option v-for="equipo in equipos" value={{equipo}}>{{equipo}}</option>
    </select>

    <p>Selecciona el segundo equipo</p>
    <select v-model="equipoA" name="" id="">
        <option v-for="equipo in equipos" value={{equipo}}>{{equipo}}</option>
    </select>

    <p>Selecciona la ronda:</p>
    <select v-model="ronda">
        <option value="1">Ronda 1</option>
        <option value="2">Ronda 2</option>
        <option value="3">Ronda 3</option>
    </select>
    <div class="SeleccionEquipos">
        <button @click="() => {
            let nuevosEquipos = [equipoA,equipoB]
            let nuevasPreguntas = []
            if(this.ronda === '1'){
                nuevasPreguntas = preguntas1
            }
            if(this.ronda === '2'){
                nuevasPreguntas = preguntas2
            }
            if(this.ronda === '3'){
                nuevasPreguntas = preguntas3
            }

            asignarPreguntasYEquipos(nuevasPreguntas,nuevosEquipos)            

        }">Jugar</button>
    </div>
</template>