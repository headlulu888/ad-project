<template>
    <v-container>
        <v-layout row>
            <v-flex xs12 sm6 offset-sm3>
                <h1 class="text--secondary mb-3">Create new ad</h1>
                <v-form v-model="valid" ref="form" validation class="mb-3">
                    <v-text-field
                      name="title"
                      label="Ad title"
                      type="text"
                      v-model="title"
                      required
                      :rules="[v => !!v || 'Title is required']"
                    ></v-text-field>
                    <v-text-field
                      name="description"
                      label="Ad description"
                      type="text"
                      v-model="description"
                      multi-line
                      :rules="[v => !!v || 'Description is required']"
                    ></v-text-field>
                    <v-layout row class="mb-3">
                        <v-flex xs12>
                            <v-btn class="warning">
                                Upload
                                <v-icon right dark>cloud_upload</v-icon>
                            </v-btn>
                        </v-flex>
                    </v-layout>
                    <v-layout>
                        <v-flex xs12>
                            <img src="" alt="" height="100">
                        </v-flex>
                    </v-layout>
                    <v-layout>
                        <v-flex xs12>
                            <v-switch
                              label="Add to promo"
                              v-model="promo"
                              color="primary"
                            >
                            </v-switch>
                        </v-flex>
                    </v-layout>
                    <v-layout>
                        <v-flex xs12>
                            <v-spacer></v-spacer>
                            <v-btn
                              :disabled="!valid"
                              class="success"
                              @click="createAd"
                            >Create ad</v-btn>
                        </v-flex>
                    </v-layout>
                </v-form>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
  export default {
    data () {
      return {
        title: '',
        description: '',
        promo: false,
        valid: false
      }
    },
    methods: {
      createAd () {
        if (this.$refs.form.validate()) {
          // logic
          const ad = {
            title: this.title,
            description: this.description,
            promo: this.promo
          }
          console.log(ad)
        }
      }
    }
  }
</script>