<script>
    export default{
        props: ['preguntas','preguntaActiva']
    }
</script>

<template>
    <div class="Pregunta card">
        <p style="margin-bottom: 1.875rem">{{preguntaActiva + 1}}) {{preguntas[preguntaActiva].preguntaTexto}}</p>
        <p><span style="color: lightblue">Dificultad: </span>{{preguntas[preguntaActiva].dificultad}}</p>
        <p><span style="color: lightblue">Categoria: </span>{{preguntas[preguntaActiva].categoria}}</p>
    </div>
</template>