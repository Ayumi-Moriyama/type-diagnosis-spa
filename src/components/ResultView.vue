<template>
  <v-card class="pa-4">
    <v-card-title class="kiwi-maru-medium">診断結果</v-card-title>
    <div v-if="result" class="wave-box-clip">
      {{ result.type }}
    </div>
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

<script setup lang="ts">
import { computed } from 'vue';

interface DiagnosisItem {
  gender: string;
  color: string;
  animal: string;
  style: string;
  type: string;
  description: string;
}

const props = defineProps<{
  gender: string;
  color: string;
  animal: string;
  style: string;
  diagnosisData: DiagnosisItem[];
}>();

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
