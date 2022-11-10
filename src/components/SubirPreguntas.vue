<script>
    export default{
        data(){
            return {
                csvText: ""
            }
        },
        methods: {
            leerPreguntas(event){
                let reader = new FileReader()
                reader.readAsText(event.target.files[0],'UTF-8')
                console.log(reader.result)
            }
        }
    }
</script>

<template>
    <div class="SubirPreguntas">
        <input @change="leerPreguntas" type="file" id="preguntascsv">
    </div>
</template>