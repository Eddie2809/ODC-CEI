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
        },
        methods: {
            empezarJuego(){
                let nuevosEquipos = [this.equipoA,this.equipoB]
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

                this.asignarPreguntasYEquipos(nuevasPreguntas,nuevosEquipos)            
                console.log(nuevosEquipos)
                this.changeRoute('Jugar')
            }
        }
    }
</script>

<template>
    <p>Selecciona el primer equipo</p>
    <select v-model="equipoB" name="" id="">
        <option v-for="equipo in equipos" :key="equipo" :value=equipo>{{equipo}}</option>
    </select>

    <p>Selecciona el segundo equipo</p>
    <select v-model="equipoA" name="" id="">
        <option v-for="equipouwu in equipos" :key=equipouwu :value=equipouwu>{{equipouwu}}</option>
    </select>

    <p>Selecciona la ronda:</p>
    <select v-model="ronda">
        <option value="1">Ronda 1</option>
        <option value="2">Ronda 2</option>
        <option value="3">Ronda 3</option>
    </select>
    <div class="SeleccionEquipos">
        <button @click="this.empezarJuego()">Jugar</button>
    </div>
</template>