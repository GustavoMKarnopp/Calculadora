<template>
    <div class="Resultado">
            <h3 class="result">{{historicoValue.valorAparente || '0'}}</h3>
          </div>
</template>
<script>
export default {

    data(){
        return{
            historicoValue: ''
    }
        }, 
        components() {
            this.historicoValue = this.$root.va
        }
        
}
</script>