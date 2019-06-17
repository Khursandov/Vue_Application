<template>
    <v-container>
        <v-layout row v-for="meetup in meetups" :key="meetup.id" class="mb-4">
    <v-flex xs12 sm6 offset-sm3>
      <v-card>
        <v-img
          :src="meetup.imageUrl"
          height="200px"
        >
        </v-img>

        <v-card-title primary-title>
          <div>
            <div class="headline">{{ meetup.title }}</div>
            <span class="grey--text">{{ meetup.date }}</span>
          </div>
        </v-card-title>

        <v-card-actions>
          <v-btn flat color="purple" :to="'/meetups/' + meetup.id">Explore</v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
    </v-container>
</template>
<script>
export default {
    computed: {
        meetups() {
            return this.$store.getters.loadedMeetups
        }
    }
}
</script>
