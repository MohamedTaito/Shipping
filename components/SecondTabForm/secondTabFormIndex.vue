<template>
  <v-form ref="form"
          v-model="isValid">
    <v-container>
      <v-row>
        <v-col class="text-left" cols="12" sm="4">
          <div class="my-2">
            <v-btn large  @click="reset">Reset X</v-btn>
          </div>
        </v-col>
      </v-row>
      <v-card class="mb-1" >
        <v-row
          class="mx-auto">
          <v-col cols="12" class="headline mb-1 pl-8">Shipping Methods</v-col>
          <v-col cols="12">
            <v-radio-group v-model="radioGroup">
              <v-radio
                label="FREE Shipping: get it by Thu, Jul 9 - Sat, Jul 11"
              ></v-radio>
              <v-radio
                label="$5.99 Standard Shipping: get it by Wed, Jul 8"
              ></v-radio>
              <v-radio
                label="$8.99 Two-Day Shipping: get it by Mon, Jul 6"
              ></v-radio>
            </v-radio-group>
          </v-col>
        </v-row>
      </v-card>
      <v-col cols="12">
        <v-checkbox
          v-model="checkbox"
          checked="checked"
          label="Item is a gift"
        ></v-checkbox>
      </v-col>
      <v-card class="mt-1" v-if="checkbox">
        <v-row
          class="mx-auto">
          <v-col cols="12" class="headline mb-1 pl-8">Shipping Methods</v-col>
          <v-col cols="12">
            <v-checkbox
              checked="checked"
              label="Include gift receipt"
            ></v-checkbox>
          </v-col>
          <v-col cols="12">
            <v-text-field
              label="Receipt Name"
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-text-field
              label="Custom Message"
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-checkbox
              checked="checked"
              label="Add gift wrap"
            ></v-checkbox>
          </v-col>
        </v-row>
      </v-card>
      <v-row>
        <v-col class="text-right" cols="12">
          <div class="my-2">
            <v-btn :disabled="!isValid" type="submit" color="primary"><nuxt-link to="/payment">Next ></nuxt-link></v-btn>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
    export default {
      data: () => ({
        checkbox: false,
        isValid: true,
        radioGroup: 0,

      }),
      methods: {
        reset () {
          this.$refs.form.reset()
        },
      },
        name: "secondTabForm"
    }
</script>

<style scoped>
a {
  text-decoration: none;
  color: #ffffff;
}
</style>
