<template>
    <div class="Resultado">
            <h3 class="result">{{historicoValue}}</h3>
    </div>
</template>
<script>
import {AppLayoutBus} from '../AppLayout.vue'
export default {

    data(){
        return{
            historicoValue: '0'
    }
    },
    created(){
        AppLayoutBus.$on('valorAparente', (valorAparente) => {
            this.historicoValue = valorAparente
        })
    },
    methods:{

    }
}
</script>