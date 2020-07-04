<template>
  <v-app light>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
  import Taps from '../components/Taps/TapsIndex'
export default {
  components: {
    Taps
  },
  data () {
    return {}
  }
}
</script>
