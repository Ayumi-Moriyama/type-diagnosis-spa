<template>
  <v-card class="pa-4">
    <v-card-title class="kiwi-maru-medium">「かっこいい」か「かわいい」どちらが好きですか？</v-card-title>
    <v-card-text class="kiwi-maru-regular">
      <div class="wave-box">
        <p>「かっこいい」は、クールなテイストです。</p>
        <p>直線的・無機質などを好む傾向があります。</p>
      </div>
      <v-divider></v-divider>
      <div class="wave-box">
        <p>「かわいい」は、キュートなテイストです。</p>
        <p>丸みを帯びた・色鮮やかなどを好む傾向があります。</p>
      </div>
      <v-divider></v-divider>
      <v-radio-group v-model="innerValue">
        <v-radio label="かっこいい" value="cool"></v-radio>
        <v-radio label="かわいい" value="cute"></v-radio>
      </v-radio-group>
    </v-card-text>
<v-btn color="primary" @click="$emit('next')" class="kiwi-maru-regular">次へ</v-btn>
  </v-card>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, computed } from 'vue';

const props = defineProps<{
  modelValue: string, // v-model のバインディング
}>();
const emit = defineEmits(['update:modelValue', 'next']);

const innerValue = computed({
  get: () => props.modelValue,
  set: (value) => emit('update:modelValue', value),
});
</script>
