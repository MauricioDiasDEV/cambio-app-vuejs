<template>
 <div>
   <h1 class="title">Reais para Dólares</h1>
   <h2 class="cifrao">$</h2>
  <div class="div-format">
   
    <span class="p-float-label">
      <InputText id="id-real" type="text" v-model="real" v-bind:disabled="cambio" />
     
      <label for="id-real">Quantidade em Reais</label>
    </span>
  </div>
  <div class="div-format">
    <span class="p-float-label">
     <InputText id="id-dolar" type="text" v-model="dolar" v-bind:disabled="cambio" />
     <label for="id-dolar">Cotação de Dólar</label>
    </span>
  </div>

  <div class="div-format" v-if="!cambio">
    <Button label="Limpar" @click="clear" />
    <Button label="Calcular" class="btn-calcular" @click="convertToDolar"/>
  </div>

  <div class="div-format" v-if="cambio != null">
    <p class="label-result">Com R$:{{real}},00 reais é possível 
      comprar U${{cambio}} dólares a U${{dolar}} cada.</p>
    
  </div>
  <div  class="div-format"  v-if="cambio != null">
    <Button  label="Calcular Novamente" @click="clear"/>
  </div>

 </div>
</template>

<script>


export default {
 data(){
   return{
     real: null,
     dolar: null,
     cambio: null
   }
 },
 methods: {
   convertToDolar: function(){
     this.cambio = (this.real / this.dolar).toFixed(2)
     console.log(this.cambio)

  
   },
   clear: function(){
     this.real = null
     this.dolar = null
     this.cambio = null
  }
 }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  
}

.div-format{
  display: flex;
  align-content: center;
  justify-content: center;
  margin-bottom: 45px ;
  
}

.title {
  text-align: center;
}
.cifrao{
  text-align: center;
  font-size: 4rem;
}

.btn-calcular{
  margin-left: 20px !important; 
}

.label-result{
  font-size: 1.5rem;
  text-align: center;
}
</style>
