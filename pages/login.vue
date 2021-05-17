<template>
  <v-container>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <v-card-title class="text-monospace">Login</v-card-title>
          <v-divider />
          <v-form ref="form" @submit.prevent="doLogin">
            <v-card-text>
              <v-text-field label="Username" />
              <v-text-field label="Password" type="password" />
            </v-card-text>
            <v-divider />
            <v-card-actions>
              <v-spacer />
              <v-btn color="primary" type="submit" :loading="loading">
                Submit
              </v-btn>
              <v-btn color="warning" @click="reset">Reset</v-btn>
            </v-card-actions>
          </v-form>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import Vue from 'vue'
import { wait } from '~/utils/misc'

export default Vue.extend({
  name: 'Login',
  data: () => ({
    form: null as any,
    loading: false
  }),
  head: {
    title: 'Login'
  },
  mounted() {
    this.form = this.$refs.form
  },
  methods: {
    doLogin() {
      this.loading = true
      this.$toast
        .$wrap(async () => {
          await wait(500)
        })
        .then(() => {
          this.loading = false
        })
    },
    reset() {
      this.form.reset()
    }
  }
})
</script>
