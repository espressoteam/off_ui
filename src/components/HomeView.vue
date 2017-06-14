<template>
  <div>
    <div class="portrait mb-1" v-for="item in items">
      <v-card :img="item.url" height="350px" @click="displayDetails(item.id)">
        <v-card-row actions class="white--text pl-3 pt-3 pb-3 headline">{{ item.name }}</v-card-row>
      </v-card>
    </div>
  </div>
</template>

<script>
import data from '../data'
export default {
  methods: {
    displayDetails(id) {
      this.$router.push({ name: 'detail', params: { id: id } })
    }
  },
  data() {
    return {
      items: data.trips
    }
  }
}
</script>

<style lang="stylus">
  .portrait
    .card__row--actions
      background: rgba(0, 0, 0, .25)
</style>
