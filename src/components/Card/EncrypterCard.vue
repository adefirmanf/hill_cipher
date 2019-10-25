<template>
  <v-card
    class="mx-auto"
    max-width="344"
    outlined
  >
    <v-list-item>
      <v-list-item-content>
        <div class="overline mb-4 red--text">ENCODE</div>
        <v-list-item-title class="headline mb-1 blue-lighten-2">
        <span class="red--text">Hill Cipher</span>
        </v-list-item-title>
        <v-divider></v-divider>
        <span class="grey--text caption font-weight-medium setMargin">KEY</span>
         <v-text-field
         v-model="keysComputed" flat solo dense full-width class="no-padding font-weight-light font-weight-medium"></v-text-field>
        <v-divider></v-divider>
        <span class="grey--text caption font-weight-medium setMargin">MATRIX SIZE</span>
        <v-select
          :items="matrixSizeList"
          v-model="matrix_size"
          label=""
          solo
          flat
          class="no-padding font-weight-medium"
        ></v-select>
        <v-simple-table
          class="hasborder setBorder"
        >
          <tbody>
          <tr v-for="(item, i) in matrixItems" :key="i" class="text-center font-weight-medium">
            <td v-for="(test, index) in Object.values(item)" :key="index">
                {{test}}
            </td>
          </tr>
        </tbody>
      </v-simple-table>
      </v-list-item-content>
    </v-list-item>
  </v-card>
</template>
<style>
  .setBorder table {
      width: 100%;
      border-collapse: collapse;
      border-spacing: 0;
  }
  .hasborder > div > table > tbody > tr > td{
    border : #e2e2e2 0.5px solid;
    height : 32px;
  }
  .setMargin {
    margin-top : 10px;
  }
</style>
<script>
  export default{
    name : '',
    props : {
      keys : String,
      matrixSize : {
        default : 2,
        type : Number
      },
      matrixSizeList : Array,
      matrixItems : Array,
      matrixChange : Function
    },
    data(){
      return {
        Msize : 2,
        hasBeenPushed : false,
      }
    },
    methods: {
    },
    computed:{
      keysComputed : {
        get(){return this.keys},
        set(value){
          this.$emit('updateKeys', value)
        }
      },
      matrix_size : {
        get(){return this.matrixSize},
        set(value){
          this.$emit('updateMatrixSize', value)
        }
      },
    },
    watch: {}
  }
</script>