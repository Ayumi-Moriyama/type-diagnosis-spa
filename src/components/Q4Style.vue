<template>
  <v-card class="pa-4">
    <v-card-title class="kiwi-maru-medium">「かっこいい」か「かわいい」どちらが好きですか？</v-card-title>
    <v-card-text class="kiwi-maru-regular">
      <v-radio-group v-model="innerValue">
        <v-radio label="かっこいい" value="cool"></v-radio>
        <v-radio label="かわいい" value="cute"></v-radio>
      </v-radio-group>
    </v-card-text>
<v-btn color="primary" @click="$emit('next')" class="kiwi-maru-regular">次へ</v-btn>
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
