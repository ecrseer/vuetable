<template>
  <table>
    <thead>
    <tr>
      <th>Nome</th>
      <th>Estado</th>
      <th>Torcida</th>
      <th>Ano</th>
      <th>info</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="item in lista">
      <td>{{ item.nome }}</td>
      <td>{{ item.estado }}</td>
      <td>{{ item.torcida }}</td>
      <td>{{ item.fundacao_ano }}</td>
      <td>{{ item.info }}</td>
    </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'TabelaMarota',
  props:['lista']
}
</script>

<style scoped>

</style>