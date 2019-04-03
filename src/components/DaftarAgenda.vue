<template>
    <div>
        <ul class="list-group list-group-flush">
            <li class="list-group-item" v-bind:key="dataAgenda.id" v-for="dataAgenda in itemAgendaBind">
                <ItemAgenda v-bind:dataAgendaBind="dataAgenda"
                            v-on:hapus-item-agenda="$emit('hapus-item-agenda',dataAgenda.id)"/>
            </li>
        </ul>
                    
        
    </div>
</template>

<script>
import ItemAgenda from './ItemAgenda.vue'

export default {
    name: 'DaftarAgenda',
    components: {
        ItemAgenda
    },
    props: [
        "itemAgendaBind"
        ]
}
</script>
