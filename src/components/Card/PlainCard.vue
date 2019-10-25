<template>
  <v-card
    class="mx-auto"
    max-width="344"
    outlined
  >
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4 blue--text">VIEW</div>
        <v-list-item-title class="headline mb-1 blue-lighten-2">
          <span class="blue--text">Text</span>
        </v-list-item-title>
        <v-divider></v-divider>
        <v-textarea v-model="message" @input="change" auto-grow flat solo full-width class="no-padding font-weight-light">
        </v-textarea>
      </v-list-item-content>
    </v-list-item>
  </v-card>
</template>

<script>
  export default{
    props : {
      message: String,
      change: Function
    }
  }
</script>