<template>
    <div>
        <div class="input-group mb-3">
            <div class="input-group-prepend">
                <div class="input-group-text">
                    <input  type="checkbox"
                            v-on:change="tandaiSelesai">
                </div>
            </div>
            <p class="form-control" style="height:100%;"
                v-bind:class="{
                    'bg-success':dataAgendaBind.selesai,
                    'text-white':dataAgendaBind.selesai
                    }">
                {{ dataAgendaBind.id + '. '+ dataAgendaBind.judul }}
            </p>
            <div class="input-group-append">
                <button class="btn btn-danger"
                        @click="$emit('hapus-item-agenda', dataAgendaBind.id)"
                        type="button">
                        x
                </button>
            </div>
        </div>
        
    </div>    
</template>

<script>
export default {
    name: "ItemAgenda",
    props: ["dataAgendaBind"],
    methods: {
        tandaiSelesai() {
            this.dataAgendaBind.selesai = !this.dataAgendaBind.selesai;
        }
    }
}
</script>
