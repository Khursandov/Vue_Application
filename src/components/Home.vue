<template>
    <v-container>
      <v-layout >
            <v-flex xs12 class="text-xs-center">
                <v-progress-circular 
                indeterminate
                 class="primary--text"
                 :width="7"
                 :size="70"
                 v-if="loading"
                 ></v-progress-circular>
            </v-flex>
        </v-layout>
    <div class="cards">
      <div class="grid">
        <div class="card" v-for="meetup in meetups" :key="meetup.id" @click="onLoadMeetup(meetup.id)">
          <img :src="meetup.imageUrl" alt="">
        </div>
      </div>
    </div>
    </v-container>
</template>
<script>
export default { 
    computed: {
        meetups() {
            return this.$store.getters.featuredMeetups
        },
        loading() {
            return this.$store.getters.loading
        }
    },
    methods: {
        onLoadMeetup(id) {
            this.$router.push('/meetups/' + id)
        }
    }
}
</script>
<style scoped>
.cards{
-webkit-box-shadow: 7px 6px 13px -8px rgba(0,0,0,0.75);
-moz-box-shadow: 7px 6px 13px -8px rgba(0,0,0,0.75);
box-shadow: 7px 6px 13px -8px rgba(0,0,0,0.75);
 width: 100%;
 background: #f4f4f4;
 border-radius: 10px;
}
.grid{
  display: grid;
  grid-gap: 10px;
  grid-template-columns: 1fr 1fr 1fr;
  padding: 30px;
}
.card {
  cursor: pointer;
  position: all 1000ms;
}
.card:hover{
  box-shadow: 3px 6px 13px 0px rgba(0,0,0,0.75);
  transition: all .2s;
}
.card img{
  width: 100%;
  background-position: center;
  height: 100% !important;
}
@media only screen and (max-width: 1000px) {
  .grid{
  display: grid;
  grid-gap: 10px;
  grid-template-columns: 1fr 1fr;
  padding: 30px;
}
}
@media only screen and (max-width: 600px) {
  .grid{
  display: grid;
  grid-gap: 10px;
  grid-template-columns: 1fr;
  padding: 30px;
}
}

</style>


