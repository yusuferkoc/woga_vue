<template>
  <div id="app" class="container">
    <div class="card" v-if="!mevcut">
      <div class="card-body"> Başlamak için butona bas</div>
       <div class="card-footer">
         <button class="btn btn-primary" @click="basla">Başla</button>
       </div>
    </div>
    <div class="card mt-10" v-else-if ="mevcut">
     <div class="card-header">{{mevcut.soru}}</div>
     <div class="card-body">
 <div class="d-flex">
         <div class="harf shadow mr-3" v-for="harf in harfler" :key="'harf-'+harf.harf">
         <span v-if="harf.acildi">{{harf.harf}}</span>
         <span v-else></span>
       </div>
 </div>
     </div>
     <div class="card-footer">Soru Puanı:{{harfPuan}}</div>
      <div class="card-footer"> Toplam Puan:{{puan}} </div>
      <div class="card-footer">
        <p>
            <input class="form-control" type="text" placeholder="Cevap yaz" >   
        </p>
   
      </div>
      <button @click="harfAl" class="btn btn-success ">Harf Al</button>
    </div>
  </div>
</template>

<script>


export default {
  name: 'app',
  components: {},
  data() {
    return{
      sorular:[
        {
          soru:"siyahın eş anlamı",
          cevap:"KARA",
          soruldu:false
        },
        {
          soru:"sık isim",
          cevap:"AHMET",
          soruldu:false
        },
        {
          soru:"tr başkent",
          cevap:"ANKARA",
          soruldu:false
        },
        {
          soru:"wizardddd ",
          cevap:"saruman",
          soruldu:false
        }
      ],
    mevcut:null,
    harfler:[],
    puan:0,
    harfPuan:0,
    userCevap:""
    };
  },

  methods: {
    basla(){
      this.mevcut = this.sorular.find(x=> !x.soruldu );
      this.mevcut.cevap.split('').map(x=>{
        this.harfler.push({
          harf:x,
          acildi:false
        });
      });
      this.harfPuan=this.harfler.length * 100;
    },
    harfAl(){
      let rastgeleHarfIndex = Math.floor(Math.random() * this.harfler.length);
      
      if (this.harfPuan <=100){
        return;
      }

      let harf = this.harfler[rastgeleHarfIndex];
      while(harf.acildi){
        rastgeleHarfIndex=Math.floor(Math.random() * this.harfler.length);
        harf=this.harfler[rastgeleHarfIndex];
      }
      console.log(rastgeleHarfIndex);
      harf.acildi=true;
      this.harfPuan -= 100;
    }
  },

}
</script>

<style>
  .harf{
    width:100px;
    height:100px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 30px;  
  }
  

</style>

