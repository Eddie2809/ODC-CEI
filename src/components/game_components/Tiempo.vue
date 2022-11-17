<script>
    export default{
        props: ['estadoTemporizador','preguntas','preguntaActiva'],
        data(){
            return{
                segundos: 15,
                milisegundos: 0,
                segundosTexto: 'Iniciar',
                interval: null,
                pausado: true,
                countdown: new Date().getTime()
            }
        },
        methods: {
            start(){
                this.segundos = this.preguntas[this.preguntaActiva].tiempo
                this.segundosTexto = String(this.segundos)

                if(this.pausado){
                    clearInterval(this.interval)
                    this.interval = setInterval(this.startTimer,0)
                }
                else{
                    clearInterval(this.interval)
                }
                this.pausado = !this.pausado
            },
            startTimer2(){
                const now = new Date().getTime()
                const distance = this.countdown - now
            },
            startTimer(){
                this.milisegundos--

                if(this.milisegundos < 0){
                    this.segundos--
                    this.segundosTexto = '0' + this.segundos
                    this.milisegundos = 99
                }
                if(this.segundos > 9){
                    this.segundosTexto = this.segundos
                }
                if(this.segundos == 0){
                    clearInterval(this.interval)
                    this.segundos = 15
                    this.segundosTexto = 'Se acabó el tiempo!'
                    this.milisegundos = 0
                }
            }
        }
    }
</script>

<template>
    <div @click="this.start()" class="Tiempo">
        <div class="box">
            <div class="loader1">
            </div>
            <p><span>{{this.segundosTexto}}</span></p>
        </div>
    </div>
</template>