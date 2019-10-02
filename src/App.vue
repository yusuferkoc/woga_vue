<template>
  <div id="app" class="container">
    <div class="card" v-if="!mevcut"></div>
    <div class="card-body">Butona</div>
    <div class="card-footer">
      <div class="btn btn-primary">başla</div>
    </div>
    <div class="card mt-25">
      <div class="card-header">Soru</div>
        <div class="card-body">
          <div class="harf">
            <span>X</span>
          </div>
          <div class="card-footer">İşlemler</div>
        </div>
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
    puan:0,
    harfPuan:0
    };
  }

}
</script>

<style>
  .harf{
    width:100px;
    height:100px;
    display: flex;
    justify-content: center;
    font-size: 30px;
    
    
  }
  .card-header{
    width:100px;
    height:100px;
    display: flex;
    justify-content: center;
    font-size: 30px;

  }
  .card-footer{
    width:100px;
    height:100px;
    display: flex;
    justify-content: center;
    font-size: 30px;

  }

</style>

