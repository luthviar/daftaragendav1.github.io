<template>
    <div>
         <div class="card-body">
            <form @submit="tambahAgendaSubmit">
            <div class="input-group mb-3">
                <input  type="text"
                        class="form-control"
                        v-model="judul"
                        name="judul"
                        placeholder="Tambahkan agenda di sini.." >
                <div class="input-group-append">
                    <button class="btn btn-outline-info" type="submit">
                        Tambah
                    </button>
                </div>
            </div>
            </form>
                
        </div>
    </div>
</template>

<script>
import uuid from "uuid";
export default {
    name: 'TambahAgenda',
    data() {
        return {
            judul: '',
            idNumber: 4
        }
    },
    methods: {
        tambahAgendaSubmit(e) {
            e.preventDefault();
            const agendaBaru = {
                // id: uuid.v4(),
                id: this.idNumber++,
                judul: this.judul,
                selesai: false
            }
            // kirim ke component di atasnya, yaitu ke App.vue
            this.$emit('tambah-agenda', agendaBaru);

            this.judul = '';
        }
    }
}
</script>
