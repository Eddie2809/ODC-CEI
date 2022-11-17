<script>
    import {equipos} from '../rondas/equipos.js'
    import {ronda1} from '../rondas/ronda1.js'
    import {ronda2} from '../rondas/ronda2.js'
    import {ronda3} from '../rondas/ronda3.js'
    import {rondaprueba} from '../rondas/rondaprueba'
    import {rondaextra1} from '../rondas/rondaextra1.js'
    import {rondaextra2} from '../rondas/rondaextra2.js'

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
                    nuevasPreguntas = ronda1
                }
                if(this.ronda === '2'){
                    nuevasPreguntas = ronda2
                }
                if(this.ronda === '3'){
                    nuevasPreguntas = ronda3
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