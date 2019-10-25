
<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Vuetify</span>
        <span class="font-weight-light">MATERIAL DESIGN</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        text
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
      >
        <span class="mr-2">Latest Release! Yeah boiii!!</span>
      </v-btn>
    </v-app-bar>
    <v-content>
      <v-row no-gutters>
        <PlainCard :message=message :change="change"/>
        <EncrypterCard 
        :matrixSize="matrixSize" 
        :matrixSizeList="matrixSizeList" 
        :keys="keys"
        @updateKeys="updateKeys"
        :matrixItems="mapMatrix"
        @updateMatrixSize="updateMatrixSize"
        ></EncrypterCard>
        <ResultCard :encrypted="enc" @updateResult="updateResult"></ResultCard>
      </v-row>
    </v-content>
  </v-app>
</template>
<style lang="scss">
  .no-padding > .v-input__control  {
     > .v-input__slot {
      padding : 0 !important;
    }
  }
</style>
<script>
/* eslint-disable no-console */
import PlainCard from './components/Card/PlainCard';
import EncrypterCard from './components/Card/EncrypterCard';
import ResultCard from './components/Card/ResultCard';

export default {
  name: 'App',
  components: {
    PlainCard, EncrypterCard, ResultCard
  },
  data: () => ({
    message : "",
    enc : "",
    keys : "helloworld",
    spliitedKeys : [],
    matrixSize : 2,
    matrixSizeList :  [{text : '2x2', value : 2}, {text : '3x3', value : 3}],
  }),
  watch:{
    mapMatrix: function(val){
      // return test
      if(val[0].length < 2){
        this.mapMatrix.push('x')
      }
    },
    keys: function(val){
      if(val.length <= 3){
        this.keys = 'xxxx'
      }
    }
  },
  computed:{
    mapMatrix: function(){
      let keys = this.spliitedKeys
      keys = this.keys.split('')
      let test = [
        [],
        []
      ]
      for(let i=0; i<keys.length; i++){
        if(i % 2 === 0){
          test[0].push(keys[i])
        }
        else{
          test[1].push(keys[i])
        }
      }
      if(keys.length % 2 !== 0){
        test[1].push('x')
      }
      return test
    }
  },
  methods: {
    change : function(msg){
      this.message = msg
      this.enc = msg
    },
    updateMatrixSize : function(value){
      this.matrixSize = value
      this.matrixItems = []
      // for(let i=0; i<this.matrixSize; i++){
      //   this.matrixItems.push(
      //     {
      //       col1 : "1",
      //       col2 : "12",
      //       col3 : "24"
      //     }
      //   )
      // }
    },
    updateKeys : function(value){
      this.keys = value
    },
    updateResult: function(value){
      this.enc = value
    }
  }
};
</script>
