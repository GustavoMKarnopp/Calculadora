<template>
    <div class="Resultado">
            <h3 class="result">{{historicoValue || '0'}}</h3>
          </div>
</template>
<script>
export default {
    data(){
        return{
            historicoValue: ''
        }
    }
}
</script>