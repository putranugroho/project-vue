<template>
  <!-- <div class="container"> -->
    <!-- <Header text="Add Task" color="blue"/> -->
  <!-- </div> -->
  <!-- <div :class="[task.reminder ? 'reminder' : '', 'task']" @dblclick="$emit('delete-task', task.id)" @click="$emit('toggle-reminder', task.id)">
        <h3>{{task.text}}</h3>
        <p>{{task.day}}</p>
    </div> -->
    <div>
      <form action="">
        <div>
          <label for="">Email</label>
          <input type="email" placeholder="Email" v-model="email"/>
        </div>
        <div>
          <label for="">Password</label>
          <input type="password" placeholder="Password" v-model="password"/>
        </div>
        <button @click="login">Login</button>
      </form>
      <hr>
      <div v-for="data in data">
        <p>{{data.kode_gudang}}</p>
        <p>{{data.nama_gudang}}</p>
        <p>{{data.alamat_gudang}}</p>
        <p>{{data.provinsi}}</p>
        <p>{{data.kabupaten_kota}}</p>
        <p>{{data.kecamatan}}</p>
        <p>{{data.kelurahan}}</p>
        <p>{{data.kodepos}}</p>
        <p>{{data.deskripsi}}</p>
        <hr>
      </div>
      <Input/>
    </div>
</template>

<script>
import Input from './components/Input'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Input
  },
  data() {
    return {
      data: [],
      token: String,
      email: '',
      password: ''
    }
  },
  created(){
    // this.data=[
    //     {
    //         "id_gudang": 1,
    //         "kode_gudang": "GD01",
    //         "nama_gudang": "gudanglagu.com",
    //         "alamat_gudang": "Kuningan",
    //         "provinsi": "DKI JAKARTA",
    //         "kabupaten_kota": "JAKARTA SELATAN",
    //         "kecamatan": "SETIABUDI",
    //         "kelurahan": "KUNINGAN TIMUR",
    //         "kodepos": 12950,
    //         "deskripsi": "ahay",
    //         "created_by": null,
    //         "updated_by": null,
    //         "status": 1
    //     },
    //     {
    //         "id_gudang": 2,
    //         "kode_gudang": "GD02",
    //         "nama_gudang": "ISTANA JANUAR MEWAH BANGET",
    //         "alamat_gudang": "DI INJEK",
    //         "provinsi": "DKI JAKARTA",
    //         "kabupaten_kota": "JAKARTA SELATAN",
    //         "kecamatan": "SETIABUDI",
    //         "kelurahan": "KUNINGAN TIMUR",
    //         "kodepos": 12950,
    //         "deskripsi": "ngipi",
    //         "created_by": "3",
    //         "updated_by": null,
    //         "status": 1
    //     },
    //     {
    //         "id_gudang": 3,
    //         "kode_gudang": "GD03",
    //         "nama_gudang": "ISTANA JANUAR SAMA SELINGKUHANNYA",
    //         "alamat_gudang": "DI INJEK",
    //         "provinsi": "DKI JAKARTA",
    //         "kabupaten_kota": "JAKARTA SELATAN",
    //         "kecamatan": "SETIABUDI",
    //         "kelurahan": "KUNINGAN TIMUR",
    //         "kodepos": 12950,
    //         "deskripsi": "GASSSS",
    //         "created_by": "3",
    //         "updated_by": null,
    //         "status": 1
    //     },
    //     {
    //         "id_gudang": 4,
    //         "kode_gudang": "GDG69",
    //         "nama_gudang": "Gudang Garam",
    //         "alamat_gudang": "Dressrosa",
    //         "provinsi": "DKI JAKARTA",
    //         "kabupaten_kota": "JAKARTA BARAT",
    //         "kecamatan": "KEBON JERUK",
    //         "kelurahan": "KEMANGGISAN",
    //         "kodepos": null,
    //         "deskripsi": "tess",
    //         "created_by": "3",
    //         "updated_by": null,
    //         "status": 1
    //     }
    // ]
  },
  methods: {
    login(){
      const data = {
        email: this.email,
        password: this.password
      }
      
      axios.post('https://api.big-solution.net/api/login', data).then(res=>this.token = res.token).catch(err=>console.log(err));
      
      const config = {
          headers: { Authorization: `Bearer ${token}` }
      };
      
      if (this.token) {
        axios.get('https://api.big-solution.net/api/admin/warehouses', config).then(res=>this.data = res.data).catch(err=>console.log(err));
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
