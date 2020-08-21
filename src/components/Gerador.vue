<template>
  <div class="col-12 py-5">
    <!-- <label for="">NÚMERO</label> -->
    <div class="form-group">
      <input type="text" v-model="numero" class="form-control" placeholder="number"/>
    </div>
    <div class="form-group">
      <!-- <label for="">MENSAGEM</label> -->
      <input type="text" v-model="mensagem" class="form-control" placeholder="messege"/>
    </div>
    <div class="">
      <button @click="Gerarlink()" class="btn btn-primary btn-lg btn-block">Gerar Link</button>
    </div>
    {{ url }}
  </div>
</template>

<script>

export default {
  name: "Gerador",
  data: function(){
    return {
      numero :"",
      mensagem: "",
      url: "",
    };
  },
  methods: {
    Gerarlink: function(){
      let n = this.numero.replace(/[^0-9]/g, '');
      let m = encodeURI(this.mensagem);
      this.url = `https://wa.me/send?phone=${n}&text=${m}`;
      this.$router.push({
        name: 'Resultado',
        params:{
          link: this.url,
        }
      });
    },
  }
};
</script>

