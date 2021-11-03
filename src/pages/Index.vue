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
      //listInstituicoes:[],
     // listConvenios:[]
      listInstituicoes:[ { "chave": "PAN", "valor": "Pan" }, { "chave": "OLE", "valor": "Ole" }, { "chave": "BMG", "valor": "Bmg" } ],
      listConvenios:[ { "chave": "INSS", "valor": "INSS" }, { "chave": "FEDERAL", "valor": "Federal" }, { "chave": "SIAPE", "valor": "Siape" } ],
      //valor simulado 5550,00
      simulator:{
        "BMG": [
          {
            "taxa": 2.05,
            "parcelas": 72,
            "valor_parcela": 144.52,
            "convenio": "INSS"
          },
          {
            "taxa": 2.05,
            "parcelas": 60,
            "valor_parcela": 167.33,
            "convenio": "INSS"
          },
          {
            "taxa": 2.05,
            "parcelas": 48,
            "valor_parcela": 195.86,
            "convenio": "INSS"
          },
          {
            "taxa": 2.05,
            "parcelas": 36,
            "valor_parcela": 261.9,
            "convenio": "INSS"
          },
          {
            "taxa": 1.9,
            "parcelas": 84,
            "valor_parcela": 135.33,
            "convenio": "INSS"
          }
        ],
        "PAN": [
          {
            "taxa": 2.05,
            "parcelas": 48,
            "valor_parcela": 190.31,
            "convenio": "INSS"
          },
          {
            "taxa": 2.08,
            "parcelas": 72,
            "valor_parcela": 157.79,
            "convenio": "INSS"
          },
          {
            "taxa": 2.1,
            "parcelas": 36,
            "valor_parcela": 173.44,
            "convenio": "FEDERAL"
          }
        ],
        "OLE": [
          {
            "taxa": 2.05,
            "parcelas": 60,
            "valor_parcela": 168.44,
            "convenio": "INSS"
          },
          {
            "taxa": 2.08,
            "parcelas": 72,
            "valor_parcela": 157.79,
            "convenio": "INSS"
          }
        ]
      }
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
