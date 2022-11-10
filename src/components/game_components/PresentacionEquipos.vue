<script>
    export default{
        props: ["equipos"]
    }
</script>

<template>
    <div class="presentacionEquipos">
        <p>{{equipos[0]}}</p>
        <p>VS</p>
        <p>{{equipos[1]}}</p>
    </div>
</template>