<template>
  <div id="app">
    
    <div class="container">
      <div class="row">
        <div class="col-lg-6 offset-lg-3">
          <div class="card text-center">
              
              <Header/>

              <TambahAgenda v-on:tambah-agenda="tambahAgendaArray"/>

              <DaftarAgenda v-bind:itemAgendaBind="itemAgendaArray" v-on:hapus-item-agenda="hapusAgenda" />

          </div> <!-- end card -->
        </div> <!-- end col -->
      </div> <!-- end row -->
    </div> <!-- end container -->
    
    

  </div>
</template>

<script>
import TambahAgenda from './components/TambahAgenda.vue';
import DaftarAgenda from './components/DaftarAgenda.vue';
import Header from './components/layouts/Header.vue';
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Header,
    TambahAgenda,
    DaftarAgenda
  },
  data() {
    return {
      itemAgendaArray: []
      // itemAgendaArray: [
      //   {
      //     id:1,
      //     judul:'Makan Nasi Goreng',
      //     selesai: false

      //   },
      //   {
      //     id:2,
      //     judul:'Tugas Matematika Diskret',
      //     selesai: false
      //   },
      //   {
      //     id:3,
      //     judul:'Tugas Transkrip Wawancara',
      //     selesai: false
      //   }
      // ]
    }
  },
  methods: {
    hapusAgenda(id) {
      this.itemAgendaArray = this.itemAgendaArray.filter(itemAgendaArray => itemAgendaArray.id !== id);
    },
    tambahAgendaArray(agendaBaru) {
      console.log('masuk array baru');
      this.itemAgendaArray = [...this.itemAgendaArray, agendaBaru];
    }
  },
  created() {
    // ini 200
    // axios.get('https://api.myjson.com/bins/7g6dk')

    // ini 10
    axios.get('https://api.myjson.com/bins/16l6i0')
        .then(res => this.itemAgendaArray = res.data)
        .catch(error => console.log(error));
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
