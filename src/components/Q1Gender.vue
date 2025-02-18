<template>
  <v-card class="pa-4">
    <v-card-title>性別を選んでください</v-card-title>
    <v-radio-group v-model="innerValue">
      <v-radio label="男性" value="male"></v-radio>
      <v-radio label="女性" value="female"></v-radio>
    </v-radio-group>
    <v-btn color="primary" @click="$emit('next')">次へ</v-btn>
  </v-card>
</template>

<script setup>
import { defineProps, defineEmits, computed } from 'vue';

const props = defineProps({
  modelValue: String, // v-model のバインディング
});
const emit = defineEmits(['update:modelValue', 'next']);

const innerValue = computed({
  get: () => props.modelValue,
  set: (value) => emit('update:modelValue', value),
});
</script>
