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
      <td v-for="(atributo,key) in item">
        {{ atributo }}
      </td>
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