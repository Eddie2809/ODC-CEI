<script>
    export default{
        props: ['equipos','puntajes']
    }
</script>

<template>
    <div class="Puntajes">
        <div class="equipoA">
            <p class="equipo">{{equipos[0]}}</p>
            <p class="puntaje">{{puntajes[0]}}</p>
        </div>
        <div class="equipoB">
            <p class="equipo">{{equipos[1]}}</p>
            <p class="puntaje">{{puntajes[1]}}</p>
        </div>
    </div>
</template>