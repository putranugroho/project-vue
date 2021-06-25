<template>
      <form action="">
        <div>
          <label for="">kode_gudang</label>
          <input type="text" placeholder="kode_gudang" v-model="kode_gudang"/>
        </div>
        <div>
          <label for="">nama_gudang</label>
          <input type="text" placeholder="nama_gudang" v-model="nama_gudang"/>
        </div>
        <div>
          <label for="">alamat_gudang</label>
          <input type="text" placeholder="alamat_gudang" v-model="alamat_gudang"/>
        </div>
        <div>
          <label for="">provinsi</label>
          <input type="text" placeholder="provinsi" v-model="provinsi"/>
        </div>
        <div>
          <label for="">kabupaten_kota</label>
          <input type="text" placeholder="kabupaten_kota" v-model="kabupaten_kota"/>
        </div>
        <div>
          <label for="">kecamatan</label>
          <input type="text" placeholder="kecamatan" v-model="kecamatan"/>
        </div>
        <div>
          <label for="">kelurahan</label>
          <input type="text" placeholder="kelurahan" v-model="kelurahan"/>
        </div>
        <div>
          <label for="">kodepos</label>
          <input type="text" placeholder="kodepos" v-model="kodepos"/>
        </div>
        <button @click="Input">Login</button>
      </form>
</template>

<script>
export default {
    name: 'Input',
    data(){
        return {
            kode_gudang: '',
            nama_gudang: '',
            alamat_gudang: '',
            provinsi: '',
            kabupaten_kota: '',
            kecamatan: '',
            kelurahan: '',
            kodepos: ''
        }
    },
  methods: {
    Input(){
      const data = {
        kode_gudang: this.kode_gudang,
        nama_gudang: this.nama_gudang,
        alamat_gudang: this.alamat_gudang,
        provinsi: this.provinsi,
        kabupaten_kota: this.kabupaten_kota,
        kecamatan: this.kecamatan,
        kelurahan: this.kelurahan,
        kodepos: this.kodepos
      }
      
      axios.post('https://api.big-solution.net/api/login', data).then(res=>this.token = res.token).catch(err=>console.log(err));
    }
  }
}
</script>