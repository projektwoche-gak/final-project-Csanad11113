<template>
  <v-card variant="outlined" class="mb-2" color="white">
    <v-card-title class="text-center">
      {{ teamOne }} vs {{ teamTwo }}
      <v-card-text> {{matchDate}} <br> {{matchLocation}} </v-card-text>
      </v-card-title>
    <v-card-actions>
    </v-card-actions>
  </v-card>
</template>

<script setup>
const props = defineProps(["teamOne", "teamTwo", "matchDate", "matchLocation"]);
</script>
