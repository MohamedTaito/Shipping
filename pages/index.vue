<template>
  <div>
    <v-tabs centered>
      <v-tab class="tab1" key="tab-1"><nuxt-link to="/"> Delivery </nuxt-link></v-tab>
      <v-tab disabled class="tab2" key="tab-2"><nuxt-link to="/shipping"> Shipping </nuxt-link></v-tab>
      <v-tab disabled class="tab3" key="tab-3"><nuxt-link to="/payment"> Payment </nuxt-link></v-tab>
    </v-tabs>
    <first-tab-form />
  </div>
</template>

<script>
  import FirstTabForm from "../components/firstTabForm/firstTabFormIndex";
export default {
  components: {
    FirstTabForm
  }
}
</script>
<style scoped>
  a {
    text-decoration: none;
  }
  .tab1 {
    border-bottom: 2px solid #1976d2;
  }
</style>
