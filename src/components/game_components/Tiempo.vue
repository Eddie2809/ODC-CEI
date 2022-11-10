<script>
    export default{
        props: ['estadoTemporizador'],
        data(){
            return{
                segundos: 15,
                milisegundos: 0,
                segundosTexto: '15',
                interval: null,
                pausado: true
            }
        },
        methods: {
            start(){
                if(this.pausado){
                    clearInterval(this.interval)
                    this.interval = setInterval(this.startTimer,0)
                }
                else{
                    clearInterval(this.interval)
                }
                this.pausado = !this.pausado
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
        <div class="contenedor">
            <p><span>{{this.segundosTexto}}</span></p>
        </div>
    </div>
</template>