<script>
    export default{
        props: ['equipos','puntajes']
    }
</script>

<template>
    <div class="puntajeFinal">
        <div class="equipoContainer">
            <p class="card equipo">{{equipos[0]}}</p>
            <p class="card puntos">{{puntajes[0]}} PUNTOS</p>
        </div>
        <div class="equipoContainer">
            <p class="card equipo">{{equipos[1]}}</p>
            <p class="card puntos">{{puntajes[1]}} PUNTOS</p>
        </div>
    </div>
</template>