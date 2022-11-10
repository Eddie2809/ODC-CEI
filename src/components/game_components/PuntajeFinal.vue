<script>
    export default{
        props: ['equipos','puntajes']
    }
</script>

<template>
    <div class="puntajeFinal">
        <div class="equipoA">
            <p>{{equipos[0]}}</p>
            <p>{{puntajes[0]}}</p>
        </div>
        <div class="equipoB">
            <p>{{equipos[1]}}</p>
            <p>{{puntajes[1]}}</p>
        </div>
    </div>
</template>