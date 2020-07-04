<template>
  <v-form
    ref="form"
    v-model="isValid"
    v-on:submit.prevent="submitForm">
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
          <v-col cols="12" class="headline mb-1 pl-8">Billing Address</v-col>
            <v-col cols="12" sm="6" md="3">
              <v-text-field
                v-model="firstName"
                :rules="nameRules"
                :counter="30"
                label="First name *"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="6" md="3">
              <v-text-field
                v-model="lastName"
                :rules="nameRules"
                :counter="30"
                label="Last name *"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12">
              <v-text-field
                v-model="firstAddress"
                :rules="address1Rules"
                :counter="120"
                label="Address Line 1 *"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12">
              <v-text-field
                v-model="secondAddress"
                :counter="120"
                label="Address Line 2"
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="6" md="3">
              <v-text-field
                v-model="city"
                :rules="nameRules"
                :counter="30"
                label="City / District *"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="6" md="3">
              <v-text-field
                v-model="state"
                :rules="nameRules"
                :counter="30"
                label="Province / State *"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="6" md="3">
              <v-text-field
                v-model="country"
                :rules="nameRules"
                :counter="30"
                label="Country *"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="6" md="3">
              <v-text-field
                v-model="postal"
                :rules="PostalRules"
                :counter="6"
                label="Postal Code *"
                required
              ></v-text-field>
            </v-col>
        </v-row>
      </v-card>
      <v-col cols="12">
        <v-checkbox
          checked="checked"
          v-model="checkbox"
          label="My shipping address is same as my billing address."
        ></v-checkbox>
      </v-col>
      <v-card class="mt-1" v-if="!checkbox">
        <v-row
          class="mx-auto">
          <v-col cols="12" class="headline mb-1 pl-8">Shipping Address</v-col>
          <v-col cols="12" sm="6" md="3">
            <v-text-field
              v-model="shippingFirstName"
              :rules="nameRules"
              :counter="30"
              label="First name *"
              type="text"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6" md="3">
            <v-text-field
              v-model="ShippingLastName"
              :rules="nameRules"
              :counter="30"
              label="Last name *"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-text-field
              v-model="shippingFirstAddress"
              :rules="address1Rules"
              :counter="120"
              label="Address Line 1 *"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-text-field
              v-model="shippingSecondAddress"
              :counter="120"
              label="Address Line 2"
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6" md="3">
            <v-text-field
              v-model="shippingCity"
              :rules="nameRules"
              :counter="30"
              label="City / District *"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6" md="3">
            <v-text-field
              v-model="shippingState"
              :rules="nameRules"
              :counter="30"
              label="Province / State *"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6" md="3">
            <v-text-field
              v-model="shippingCountry"
              :rules="nameRules"
              :counter="30"
              label="Country *"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6" md="3">
            <v-text-field
              v-model="shippingPostal"
              :rules="PostalRules"
              :counter="6"
              label="Postal Code *"
              type="number"
              required
            ></v-text-field>
          </v-col>
        </v-row>
      </v-card>
      <v-col cols="12">
        <v-radio-group v-model="radioGroup">
          <v-row>
            <v-col cols="12" sm="6" md="3">
              <v-radio @change="handleRadio()"
                label="Create Account"
              ></v-radio>
            </v-col>
            <v-col cols="12" sm="6" md="3">
              <v-radio @change="handleRadio()"
                label="Checkout as a Guest"
              ></v-radio>
            </v-col>
          </v-row>
        </v-radio-group>
      </v-col>
      <v-card class="mt-1" v-if="radioGroup == 0">
        <v-row
          class="mx-auto">
          <v-col cols="12">
            <v-text-field
              v-model="email"
              :rules="emailRules"
              :counter="50"
              label="Email *"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6" md="3">
            <v-text-field
              v-model="password"
              :rules="passwordRules"
              :counter="30"
              label="Password *"
              type="password"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6" md="3">
            <v-text-field
              v-model="confirmPassword"
              :rules="passwordConfirmationRule"
              :counter="30"
              type="password"
              label="Confirm Password *"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            Minimum eight characters, at least one uppercase letter, one lowercase letter, one number and one special character (@$!%*#?&)
          </v-col>
        </v-row>
      </v-card>
      <v-card class="mt-1" v-if="radioGroup == 1">
        <v-row
          class="mx-auto">
          <v-col cols="12">
            <v-text-field
              v-model="email"
              :rules="emailRules"
              :counter="50"
              label="Email *"
              required
            ></v-text-field>
          </v-col>
        </v-row>
      </v-card>
      <v-row>
        <v-col class="text-right" cols="12">
          <div class="my-2">
            <v-btn :disabled="!isValid" type="submit" color="primary">Next ></v-btn>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
    export default {
      data: () => ({
        error: {},
        isValid: true,
        firstName: '',
        lastName: '',
        firstAddress: '',
        secondAddress: '',
        city: '',
        state: '',
        country: '',
        postal: '',
        shippingFirstName: '',
        ShippingLastName: '',
        shippingFirstAddress: '',
        shippingSecondAddress: '',
        shippingCity: '',
        shippingState: '',
        shippingCountry: '',
        shippingPostal: '',
        checkbox: true,
        radioGroup: 0,
        is_new_account: 0,
        email: '',
        password: '',
        confirmPassword: '',
        nameRules: [
          v => !!v || 'This field is required',
          v => (v && v.length <= 30) || 'This field must be less than 31 characters',
        ],
        address1Rules: [
          v => !!v || 'This field is required',
          v => (v && v.length <= 120) || 'This field must be less than 121 characters',
        ],
        PostalRules: [
          v => !!v || 'This field is required',
          v => (v && v.length <= 6) || 'This field must be less than 7 numbers',
          v => (v && v.length >= 3) || 'This field must be at least 3 numbers',
          v => /^[0-9]*$/.test(v) || 'Only numbers required',
        ],
        emailRules: [
          v => !!v || 'E-mail is required',
          v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
        ],
        passwordRules: [
          v => !!v || 'This field is required',
          v => (v && v.length <= 30) || 'This field must be less than 31 characters',
          v => (v && v.length >= 8) || 'This field must be at least 8 characters',
          v => /[a-z]+/.test(v) || 'One lowercase letter required',
          v => /[A-Z]+/.test(v) || 'One uppercase letter required',
          v => /[0-9]+/.test(v) || 'One number required',
          v => /[!@#$%&*]/.test(v) || 'One special character required',
        ],
      }),
      computed: {
        passwordConfirmationRule() {
          return [(this.password === this.confirmPassword) || 'Password must match']
        },
      },
      methods:{
        reset () {
          this.$refs.form.reset()
        },
        handleRadio() {
          let newValue = this.radioGroup != 0 ? 0 : 1
          this.is_new_account = newValue
        },
        submitForm(){
          let newValue = this.checkbox == true ? 0 : 1
          this.$axios.$post('/saveAddress' , {
            first_name:this.firstName,
            last_name:this.lastName,
            address_1:this.firstAddress,
            address_2:this.secondAddress,
            city:this.city,
            state:this.state,
            country:this.country,
            postal_code:this.postal,
            is_same_address:newValue,
            shipping_first_name:this.shippingFirstName,
            shipping_last_name:this.ShippingLastName,
            shipping_address_1:this.shippingFirstAddress,
            shipping_address_2:this.shippingSecondAddress,
            shipping_city:this.shippingCity,
            shipping_state:this.shippingState,
            shipping_country:this.shippingCountry,
            shipping_postal_code:this.shippingPostal,
            is_new_account:this.is_new_account,
            email:this.email,
            password:this.password,
            password_confirmation:this.confirmPassword,
          })
            .then(res => {
              this.$router.push('/shipping')

            }).catch(error => {
              this.error =  error.message;
          })
        }
      },
        name: "firstTapForm"
    }
</script>

<style scoped>

</style>
