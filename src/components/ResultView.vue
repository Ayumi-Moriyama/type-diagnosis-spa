<template>
  <v-card class="pa-4">
    <v-card-title>診断結果</v-card-title>
    <v-card-text v-if="result">
      あなたのタイプは <strong>{{ result.type }}</strong> です！
    </v-card-text>
    <v-card-text v-else>
      診断結果が見つかりませんでした。
    </v-card-text>
  </v-card>
  <v-btn color="primary" @click="$emit('restart')">再診断する</v-btn>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  gender: String,
  color: String,
  animal: String,
  style: String,
  diagnosisData: Array,
});

const result = computed(() =>
  props.diagnosisData.find(
    (item) =>
      item.gender === props.gender &&
      item.color === props.color &&
      item.animal === props.animal &&
      item.style === props.style
  )
);
</script>
