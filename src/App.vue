<template>
  <h3>Times</h3>

<h1>tabela times</h1>
  <TabelaMarota :lista="times"></TabelaMarota>

  <h2>tabela alunos</h2>
  <TabelaMarota :lista="alunos"></TabelaMarota>


  <div>

    <Campo nome="nome" v-model="time.nome"></Campo>
    <CampoDropDown nome="estado" v-model="time.estado" :itens="estados"></CampoDropDown>
    <Campo nome="tecnico" v-model="time.tecnico"></Campo>
    <Campo nome="torcida" tipo="number" v-model="time.torcida"></Campo>
    <Campo nome="fundacao" tipo="number" v-model="time.fundacao_ano"></Campo>
    <CampoText tipo="texto" nome="info" v-model="time.info"></CampoText>

    <span v-if="carregando">carregando...</span>
    <button v-else @click="salvar">salvar</button>
  </div>

</template>


<script>
// todo:
// atualizar lista superior
// limpar campos depois de salvar
// estados como drop-down
// torcida tem q ser do tipo number
// fundacao do tipo number
// info tem q ser um textarea

// transformar a listagem de times em uma tabela
// excluir
// editar um time

import Campo from './components/Campo.vue'
import axios from 'axios'
import CampoDropDown from './components/CampoDropDown.vue'
import CampoText from './components/CampoText.vue'
import TabelaMarota from "./components/TabelaMarota.vue";

let timeNovo = () => {
  return {
    'id': 'INCREMENT',
    'nome': '',
    'estado': '',
    'tecnico': '',
    'torcida': '',
    'fundacao_ano': '',
    'info': ''
  }
}

let alunoNovo = () => {
  return {
    'id': 'INCREMENT',
    'nome': '',
    'serie': '',
    'idade': '',
  }
}


export default {
  components: {TabelaMarota, CampoText, CampoDropDown, Campo},
  data() {
    return {
      time: timeNovo(),
      times: [],
      alunos:[
        {
          'id': 'INCREMENT',
          'nome': 'mock1',
          'serie': 'mock2',
          'idade': 'mock3',
        },
        {
          'id': 'INCREMENT',
          'nome': 'm2',
          'serie': 'm3',
          'idade': '5',
        },
        {
          'id': 'INCREMENT',
          'nome': 'a2',
          'serie': 'a3',
          'idade': 'mock3',
        },
      ],
      carregando: true,
      estados: [
        'RJ',
        'SP',
        'RS',
      ]
    }
  },
  methods: {
    salvar() {
      this.carregando = true
      axios.post(
          'https://sheetdb.io/api/v1/87jz1jtmjtrf6',
          {data: [this.time]}
      ).then(() => {
        this.times.push(this.time)
        this.time = timeNovo()
        this.carregando = false
      })
    }
  },
  mounted() {
    this.carregando = true
    axios.get('https://sheetdb.io/api/v1/87jz1jtmjtrf6').then(({data}) => {
      this.times = data
      this.carregando = false
    })
  }
}
</script>

<style>


</style>
