<script>
    export default{
        props: ["equipos"]
    }
</script>

<template>
    <div class="presentacionEquipos">
        <h1 class="equipoA">
            <span>{{equipos[0]}}</span>
            <span>{{equipos[0]}}</span>
        </h1>
        <h2>VS</h2>
        <h1 class="equipoB">
            <span>{{equipos[1]}}</span>
            <span>{{equipos[1]}}</span>
        </h1>
    </div>
</template>