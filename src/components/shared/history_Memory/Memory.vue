<template>
    <main>
        <v-list-item
            v-for="item in items"
            :key="item.title"
            link
            >
            <v-list-item-content>
                <h1>Memory</h1>
                <v-list-item-title class="mt-5">{{ item.dados }}</v-list-item-title>
            <div class="BotoesF1" cols="2">
                <button class="bts"> MC </button>
                <button class="bts"> MR </button>
                <button class="bts"> M+ </button>
                <button class="bts"> M- </button>
                <button class="bts"> MS </button>
                <button class="bts"> M </button>                  
            </div>
            </v-list-item-content>
        </v-list-item>
    </main>
</template>
<script>
export default {
    components:{
    },
    data () {
    
    return {
        drawer: null,
        items: [
            { dados: '15 + 2 + 4 + 5 ' },
        ],
        }
    },
}
</script>   