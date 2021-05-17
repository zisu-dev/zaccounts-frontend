<template>
  <v-container>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <v-card-title>
            <div>Profile</div>
            <v-spacer />
            <v-btn-toggle v-model="editMode">
              <v-btn :value="true">Edit</v-btn>
            </v-btn-toggle>
          </v-card-title>
          <v-divider />
          <template v-if="editMode">
            <v-card-text>
              <v-text-field v-model="newProfile.disp" label="display name" />
              <v-text-field v-model="newProfile.email" label="email" />
              <v-text-field v-model="newProfile.website" label="website" />
              <v-textarea v-model="newProfile.bio" label="bio" />
            </v-card-text>
            <v-card-actions>
              <v-spacer />
              <v-btn color="warning">Cancel</v-btn>
              <v-btn color="primary">Update</v-btn>
            </v-card-actions>
          </template>
          <template v-else>
            <v-card-title>
              <v-spacer />
              <v-avatar size="128">
                <v-img :src="getAvatar(profile.email)" />
              </v-avatar>
              <v-spacer />
            </v-card-title>
            <v-divider />
            <v-card-title>
              <div>
                <div class="text-h4">{{ profile.disp }}</div>
                <div class="text-h6 text--secondary">{{ profile.email }}</div>
              </div>
            </v-card-title>
            <template v-if="profile.bio">
              <v-divider />
              <v-card-text>
                {{ profile.bio }}
              </v-card-text>
            </template>
            <v-divider />
            <v-list dense>
              <v-list-item>
                <v-list-item-avatar size="24">
                  <v-icon>{{ mdiEmail }}</v-icon>
                </v-list-item-avatar>
                <v-list-item-content>
                  <v-list-item-title class="text-none">
                    {{ profile.email }}
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </template>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { mdiEmail } from '@mdi/js'
import Vue from 'vue'
import { gravatar } from '~/utils/gravatar'

export default Vue.extend({
  name: 'Profile',
  data: () => ({
    editMode: false,
    profile: {
      name: 'thezzisu',
      disp: 'Zisu Zhang',
      email: 'i@zzs1.cn',
      bio: 'Foobar'
    },
    newProfile: {},
    mdiEmail
  }),
  head: {
    title: 'Profile'
  },
  methods: {
    getAvatar: gravatar
  }
})
</script>
