<script>
    export default{
        props: ['opciones','preguntaActiva','subirRespuesta'],
    }
</script>

<template>
    <div class="Opciones">
        <div @click="subirRespuesta(1)" class="opcion card"><p>A) <span>{{opciones.opcion1}}</span></p></div>
        <div @click="subirRespuesta(2)" class="opcion card"><p>B) <span>{{opciones.opcion2}}</span></p></div>
        <div @click="subirRespuesta(3)" class="opcion card"><p>C) <span>{{opciones.opcion3}}</span></p></div>
        <div @click="subirRespuesta(4)" class="opcion card"><p>D) <span>{{opciones.opcion4}}</span></p></div>
    </div>
</template>