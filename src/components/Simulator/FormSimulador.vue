<template>
  <div class="form">
    <q-form
      @submit="handleSubmit"
    >
      <div>
        <q-input 
         v-model="form.valor_emprestimo" 
         label="Valor do empréstimo" 
         stack-label
         dense
         mask="#.##"
         fill-mask="0"
         reverse-fill-mask
         :rules="[val => !!val || 'Informe o valor para a simulação']"
          />
      </div>
      <div>
        <q-select
          v-model="form.instituicoes"
          label="Instituição"
          :options="listInstituicoes"
          option-value="chave"
          option-label="valor"
          option-disable="inactive"
          emit-value
          map-options
          dense
          multiple
        />
      </div>
      <div>
        <q-select
          v-model="form.convenios"
          label="Convênio"
          :options="listConvenios"
          option-value="chave"
          option-label="valor"
          option-disable="inactive"
          emit-value
          map-options
          dense
          multiple
        />
      </div>
      <div>
        <q-select
          v-model="form.parcela"
          label="Parcelas"
          :options="listParcelas"
          option-disable="inactive"
          emit-value
          map-options
          dense
        />
      </div>
      <div class="btn-form">
        <q-btn 
        color="primary" 
        label="Simular"
        type="submit"
         />
      </div>
    </q-form> 
  </div>
</template>
<script>
export default {
  name:"FormSimulator",
  props:["listInstituicoes","listConvenios"],
  data(){
    return{
      listParcelas:[36, 48, 60, 72, 84],
      form:{
        "valor_emprestimo":'',
        "instituicoes":[],
        "convenios":[],
        "parcela":""
      }
    }
  },
  methods:{
    handleSubmit(){
      this.$emit("postSimulator",this.form)
    }
  }
}
</script>

<style>
  .form{
    width: 300px;
    margin: 0 auto;
    margin-top: 15px
  }
  .btn-form{
    text-align: center;
    margin: 7px;

  }
</style>