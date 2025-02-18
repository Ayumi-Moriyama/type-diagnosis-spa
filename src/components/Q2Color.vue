<template>
  <v-card class="pa-4">
    <v-card-title>好きな色を選んでください</v-card-title>
    <v-card-text>
      <v-radio-group v-model="innerValue">
        <v-radio label="赤" value="red"></v-radio>
        <v-radio label="青" value="blue"></v-radio>
        <v-radio label="緑" value="green"></v-radio>
      </v-radio-group>
    </v-card-text>
    <v-btn color="primary" @click="$emit('next')">次へ</v-btn>
  </v-card>
</template>

<script setup>
import { defineProps, defineEmits, computed} from 'vue';

const props = defineProps({
  modelValue: String, // v-model のバインディング
});
const emit = defineEmits(['update:modelValue', 'next']);

const innerValue = computed({
  get: () => props.modelValue,
  set: (value) => emit('update:modelValue', value),
});
</script>
