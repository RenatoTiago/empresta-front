<template v-if="!!simulator">
<div class="bodyTable" v-if="!!simulator.PAN">
  <div class="row">
    <div class="col-12 title">Pan</div>
  </div>
  <hr/>
  <div class="row lines title">
    <div class="col-3">Taxa</div>
    <div class="col-3">Parcelas</div>
    <div class="col-3">Valor das Parcelas</div>
    <div class="col-3">Convênio</div>
  </div>
  <div class="row lines" v-for="simulation in simulator.PAN" :key="simulation">
    <div class="col-3">{{simulation.taxa}}%</div>
    <div class="col-3 text-focus">{{simulation.parcelas}}x</div>
    <div class="col-3">R$ {{simulation.valor_parcela}}</div>
    <div class="col-3">{{simulation.convenio}}</div>
  </div>
</div>
<div class="bodyTable" v-if="!!simulator.PAN">
  <div class="row">
    <div class="col-12 title">Ole</div>
  </div>
  <hr/>
  <div class="row lines title">
    <div class="col-3">Taxa</div>
    <div class="col-3">Parcelas</div>
    <div class="col-3">Valor das Parcelas</div>
    <div class="col-3">Convênio</div>
  </div>
  <div class="row lines" v-for="simulation in simulator.OLE" :key="simulation">
    <div class="col-3">{{simulation.taxa}}%</div>
    <div class="col-3 text-focus">{{simulation.parcelas}}x</div>
    <div class="col-3">R$ {{simulation.valor_parcela}}</div>
    <div class="col-3">{{simulation.convenio}}</div>
  </div>
</div>
<div class="bodyTable" v-if="!!simulator.PAN">
  <div class="row">
    <div class="col-12 title">BMG</div>
  </div>
  <hr/>
  <div class="row lines title">
    <div class="col-3">Taxa</div>
    <div class="col-3">Parcelas</div>
    <div class="col-3">Valor das Parcelas</div>
    <div class="col-3">Convênio</div>
  </div>  
  <div class="row lines" v-for="simulation in simulator.BMG" :key="simulation">
    <div class="col-3">{{simulation.taxa}}%</div>
    <div class="col-3 text-focus">{{simulation.parcelas}}x</div>
    <div class="col-3">R$ {{simulation.valor_parcela}}</div>
    <div class="col-3">{{simulation.convenio}}</div>
  </div>
</div>
</template>
<script>
export default {
  name:"TableSimulador",
  props:["simulator","listInstituicao"],
}
</script>
<style scoped>
  .bodyTable{
    margin: 10px auto;
    border: 1px solid rgb(102, 102, 102);
    padding: 5px;
    width: 50rem;
  }
  .title{
    font-weight: bold;
    font-size: 1em;
  }
  .text-focus{
    font-style: italic;
    font-weight: 400;
    text-decoration: underline;
  }
  .lines{

  }
</style>