<template>
  <v-card class="pa-4">
    <v-card-title class="kiwi-maru-medium">診断結果</v-card-title>
    <v-card-text v-if="result" class="kiwi-maru-regular">
      <p>あなたのタイプは <strong>{{ result.type }}</strong> です！</p>
      <p>あなたは {{ result.description }} といった特徴を持つ傾向があります。</p>
    </v-card-text>
    <v-card-text v-else class="kiwi-maru-regular">
      診断結果が見つかりませんでした。
    </v-card-text>
  </v-card>
  <v-btn color="primary" @click="$emit('restart')" class="kiwi-maru-medium">再診断する</v-btn>
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
