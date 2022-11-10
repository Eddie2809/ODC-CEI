<script>
    export default{
        data(){
            return{
            }
        },
        props: ['changeRoute']
    }
</script>

<template>
    <div class="Home">
        <div class="menu" >
            <button class="main-btn"  @click="this.changeRoute('Jugar')">Jugar</button>
            <button @click="this.changeRoute('SubirPreguntas')">Subir preguntas</button>
            <button>Ver preguntas</button>
            <button>Configuraciones</button>
        </div>
    </div>
    
</template>