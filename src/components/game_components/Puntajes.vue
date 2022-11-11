<script>
    export default{
        props: ['equipos','puntajes','turno']
    }
</script>

<template>
    <div class="Puntajes">
        <div class="equipoA">
            <p :class="turno == 0? 'equipo equipoTurno':'equipo'" >{{equipos[0]}}</p>
            <p class="puntaje">{{puntajes[0]}}</p>
        </div>
        <div class="equipoB">
            <p :class="turno == 1? 'equipo equipoTurno':'equipo'">{{equipos[1]}}</p>
            <p class="puntaje">{{puntajes[1]}}</p>
        </div>
    </div>
</template>