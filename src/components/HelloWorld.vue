<template>
  <div class="hello">
    <h1 v-if="isShowName">
    halo nama saya <span v-html="fristname"></span> dan {{lastname}}
    </h1>
    <p>
    saya tinggal di {{address.city}} provinsi {{address.provinsi}}
    </p>
   <p>
    tahun depan saya berumur {{age + 1}} tahun
   </p>
   <p>
    saya
    <span v-if="age < 10 && age > 0"> masih anak kecil</span>
    <span v-else-if="age < 20 && age > 10">Sudah remaja</span>
    <span v-else>tua</span>
   </p>
   <p>
    saya {{work ? 'bekerja' : 'Tidak bekerja'}}
   </p>
   <p>
      <a :href="facebookurl" :title="title">facebook</a><br>
  </p>
  <p>
      <button :disabled="buttonState" v-on:click="showPopUp()">
        klik
      </button>
   </p>
   <p>
    <button @click="showName()">
      show
    </button>
   </p>
   <p>
      <ul>
          <li v-for="makan in daftarMakan" :key="makan.id">
                {{makan.namamakan}}
          </li>
      </ul>
   </p>
   <p>
      umur saya {{getMyAge}}
   </p>
   <p>
      {{getAddresData}}
   </p>
   <p>
      <input type="text" name="fristname" v-model="fristname">
      <input type="text" name="lastname" v-model="lastname">
       <input type="text" name="city" v-model="address.city">
       <input type="text" name="provinsi" v-model="address.provinsi">
   </p>
   <p>
    <input type="number" v-model="myborn">
   </p>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      fristname: "Egi",
      lastname: "Permana",
      age: 25,
      myborn: 1992,
      work: true,
      address: {
        city: "Bandung",
        provinsi: "Jawa Barat",
        country: "indonesia"
      },
      facebookurl: "https://facebook.com",
      title: "wew facebook again",
      buttonState: false,
      isShowName: true,
      daftarMakan: [
        { id: 1, namamakan: "bakso" },
        { id: 2, namamakan: "apel" },
        { id: 3, namamakan: "buah" }
      ]
    };
  },
  methods: {
    showPopUp() {
      alert("hello");
    },
    showName() {
      this.isShowName = !this.isShowName;
    }
  },
  computed: {
    getMyAge() {
      let currentdate = new Date().getFullYear();
      let myborn = this.myborn;
      let year = currentdate - myborn;
      return year;
    },
    getAddresData() {
      let { city, provinsi, country } = this.address;
      return city + " " + provinsi + " " + country;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
