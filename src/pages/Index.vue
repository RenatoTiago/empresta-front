<template>
  <Header />

  <FormSimulador
   :listInstituicoes="listInstituicoes"
   :listConvenios="listConvenios"
   @postSimulator="postSimulator"
  />

  <TableSimulador
    :listInstituicoes="listInstituicoes"
    :simulator="simulator"
  />
</template>

<script>
import Header from "../components/header"
import axios from "axios"
import FormSimulador from '../components/Simulator/FormSimulador.vue'
import TableSimulador from "../components/Simulator/TableSimulador.vue"

export default {
  name: 'Index',
  components: {
    Header,
    FormSimulador,
    TableSimulador
  },
  data(){
    return{
      listInstituicoes:[],
     listConvenios:[],
      simulator:[]
    }
  },
  methods:{
    postSimulator(form){
      console.log(form.valor_emprestimo)
      console.log(this.similator)
      debugger
      let body = form;
      let headers = {
        'Access-Control-Allow-Origin': '*'
      }
      axios
      .post("http://127.0.0.1:8000/api/simular", body,headers)
      .then(res => {
        this.similator = res.data
        console.log(res)
      })
      .catch((err) => {
        console.log(err)
      })
    },
    getInstituicoes(){
      let headers = {
        'Access-Control-Allow-Origin': '*'
      }
      axios
      .get("http://127.0.0.1:8000/api/instituicao", headers)
      .then(res => {
        this.listInstituicoes= res.data
      })
      .catch((err) => {
        console.log(err)
      })
    },

    getConvenios(){
      let headers = {
        'Access-Control-Allow-Origin': '*'
      }
      axios
      .get("http://127.0.0.1:8000/api/convenio", headers)
      .then(res => {
        this.listConvenios = res.data
      })
      .catch((err) => {
        console.log(err)
      })
    }
  },
  created(){
    this.getInstituicoes()
    this.getConvenios()
  }
}
</script> 
<style>

</style>
