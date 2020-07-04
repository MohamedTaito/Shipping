<template>
 <div>
   <v-tabs centered>
     <v-tab class="tab1" key="tab-1"><nuxt-link to="/"> Delivery </nuxt-link></v-tab>
     <v-tab class="tab2" key="tab-2"><nuxt-link to="/shipping"> Shipping </nuxt-link></v-tab>
     <v-tab class="tab3" key="tab-3"><nuxt-link to="/payment"> Payment </nuxt-link></v-tab>
   </v-tabs>
   <second-tab-form />
 </div>
</template>

<script>
  import SecondTabForm from  "../../components/secondTabForm/secondTabFormIndex"
    export default {
    components: {
      SecondTabForm
    },
      name: "index"
    }
</script>

<style scoped>
  a {
    text-decoration: none;
  }
.tab2 {
  border-bottom: 2px solid #1976d2;
}
</style>
