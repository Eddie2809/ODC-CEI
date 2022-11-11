<script>
    export default{
        props: ['equipos','puntajes']
    }
</script>

<template>
    <div class="puntajeFinal">
        <div class="equipoA">
            <p class="card">{{equipos[0]}}</p>
            <p class="card">{{puntajes[0]}}</p>
        </div>
        <div class="equipoB">
            <p class="card">{{equipos[1]}}</p>
            <p class="card">{{puntajes[1]}}</p>
        </div>
    </div>
</template>