<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <h1>Unit Converter</h1>
      </div>

      <v-spacer></v-spacer>
      <v-btn
        href="https://github.com/Drywock/unit-converter/tree/master"
        target="_blank"
        text
      >
        <span class="mr-2">Source Code</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <v-container>
        <v-row justify="center" align="center">
          <v-col>
          <h1>1. Name Unit</h1>
          <v-text-field outlined
            label="Unit Name"
            v-model="mainUnitName"
          />

          <h1>2. Set Convertion</h1>
          <v-row 
            justify="center"
            align-items="center"
            class="flex-column"
          >
            <convertionEditor v-for="(convertion, index) in convertions"
              :key="index"
              :convertion="convertion"
              :mainUnitName="mainUnitName"
            />
            <v-btn @click="addConvertion">Add Convertion</v-btn>
          </v-row>

          <h1>3. Unit converter</h1>
          <v-text-field v-model="value" type="number" :suffix="mainUnitName" />
          <ul>
            <convertion-display-item v-for="(convertion, index) in convertions" :key="index"
              :name="convertion.name" 
              :ratio="convertion.ratio" 
              :input="value"
            />
          </ul>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import ConvertionDisplayItem from '@/components/ConvertionDisplayItem.vue';
import ConvertionEditor from '@/components/ConvertionEditor.vue';

export default {
  name: 'App',
  components: {
    ConvertionDisplayItem,
    ConvertionEditor
  },

  data: () => ({
    mainUnitName: "",
    value: undefined,
    convertions: []
  }),
  methods: {
    addConvertion() {
      this.convertions.push({
        name: "",
        ratio: undefined,
      });
    }
  }
};
</script>
