<template>
  <v-row justify="center">
    <v-text-field placeholder="Ratio"
      v-model="convertion.ratio"
      type="number"
      class="flex-grow-0"
      :prefix="'1 ' + mainUnitName + ' = ' "
    />
    <v-text-field placeholder="Name"
      v-model="convertion.name"
      class="flex-grow-0"
    />
  </v-row>
</template>

<script>
  export default {
    props: ["convertion" , "mainUnitName"]
  }
</script>