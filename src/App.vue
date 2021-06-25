<template>
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
