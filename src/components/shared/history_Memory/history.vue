<template>
    <main>
        <v-list-item
            v-for="item in items"
            :key="item.title"
            link
        >
            <v-list-item-content>
                <h1>History</h1>
                <v-list-item-title class="mt-5">{{ item.dados }}</v-list-item-title>
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