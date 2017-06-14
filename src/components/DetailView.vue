<template>
  <div>
    <v-card horizontal>
      <v-card-column class="brown white--text">
        <v-card-row>
          <v-btn icon dark @click.native.stop="goBack">
            <v-icon>chevron_left</v-icon>
          </v-btn>
          <v-spacer></v-spacer>
          <v-card-text class="text-xs-right">
            <h4 class="white--text">{{item.name}}</h4>
            <div class="caption">{{item.info}}</div>
          </v-card-text>
        </v-card-row>
      </v-card-column>
      <v-card-row :img="item.url" height="200px"></v-card-row>
    </v-card>
    <v-layout row wrap>
      <v-flex xs12 md8 offset-md2>
        <v-stepper class="" v-model="index" vertical>
          <template v-for="(step, i) in item.steps">
            <v-stepper-step :step="i+1" v-bind:complete="index > i+1" @click.native="index = i+1">
              {{step.name}}
            </v-stepper-step>
            <v-stepper-content :step="i+1">
              <div class="caption mb-1">
                <v-icon>photo_camera</v-icon>
                {{step.info}}
              </div>
              <v-card>
                <v-card-row :img="step.url" class="grey lighten-1 z-depth-1" height="200px"></v-card-row>
                <v-card-row actions class="blue-grey darken-1 mt-0">
                  <v-btn flat class="white--text" @click.native="index = i+2">Continue</v-btn>
                  <v-spacer></v-spacer>
                  <v-btn icon>
                    <v-icon class="white--text">explore</v-icon>
                  </v-btn>
                </v-card-row>
              </v-card>
            </v-stepper-content>
          </template>
        </v-stepper>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import data from '../data'
export default {
  methods: {
    goBack() {
      this.$router.go(window.history.back())
    }
  },
  data() {
    return {
      index: 1,
      item: data.trips[this.$route.params.id]
    }
  }
}
</script>

<style>

</style>
