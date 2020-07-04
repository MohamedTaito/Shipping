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
          <v-col cols="12" class="headline mb-1 pl-8">Payment Method</v-col>
          <v-col cols="12" sm="6" md="3">
            <v-text-field
              v-model="CardNumber"
              :rules="CardRules"
              label="Card Number *"
              :counter="16"
              required
            ></v-text-field>
          </v-col>
          <v-row class="col-12">
            <v-col cols="12" sm="6" md="3">
              <v-menu
                v-model="fromDateMenu"
                :close-on-content-click="false"
                :nudge-right="40"
                transition="scale-transition"
                offset-y
                max-width="290px"
                min-width="290px"
              >
                <template v-slot:activator="{ on }">
                  <v-text-field
                    label="Expire Date *"
                    readonly
                    :value="fromDateDisp"
                    v-on="on"
                    :rules="DateRules"
                    required
                  ></v-text-field>
                </template>
                <v-date-picker
                  locale="en-in"
                  v-model="fromDateVal"
                  no-title
                  @input="fromDateMenu = false"
                  :min="minDate"
                ></v-date-picker>
              </v-menu>
            </v-col>
            <v-col cols="12" sm="6" md="3">
              <v-text-field
                v-model="cvv"
                :rules="CvvRules"
                :counter="3"
                label="CVV *"
                required
              ></v-text-field>
            </v-col>
          </v-row>
        </v-row>
      </v-card>
      <v-row>
        <v-col class="text-right" cols="12">
          <div class="my-2">
            <v-btn :disabled="!isValid" color="primary"><nuxt-link to="/Done">Pay</nuxt-link></v-btn>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
    export default {
      data: () => ({
        CardNumber: '',
        cvv: '',
        fromDateMenu: false,
        fromDateVal: null,
        minDate: "2020-07",
        isValid: true,
        CardRules: [
          v => !!v || 'This field is required',
          v => (v && v.length <= 16) || 'This field must be less than 17 number',
          v => (v && v.length >= 16) || 'This field must be 16 number',
          v => /^[0-9]*$/.test(v) || 'Only numbers required',
        ],
        CvvRules: [
          v => !!v || 'This field is required',
          v => (v && v.length <= 3) || 'This field must be less than 4 number',
          v => (v && v.length >= 3) || 'This field must be 3 number',
          v => /^[0-9]*$/.test(v) || 'Only numbers required',
        ],
        DateRules: [
          v => !!v || 'This field is required',
        ],

      }),
      methods: {
        reset () {
          this.$refs.form.reset()
        },
      },
      computed: {
        fromDateDisp() {
          return this.fromDateVal;

        }
      },
        name: "thirdTabFormIndex"
    }
</script>

<style scoped>
  a {
    text-decoration: none;
    color: #ffffff;
  }
</style>
