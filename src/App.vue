<template>
  <v-app>
    <v-container>
      <v-card class="pa-4" v-if="step === 0">
        <v-card-title class="kiwi-maru-medium">タイプ診断</v-card-title>
        <v-card-text class="kiwi-maru-regular">質問に答えてあなたのタイプを診断しましょう。</v-card-text>
        <v-btn color="primary" @click="startDiagnosis" class="kiwi-maru-medium">診断を開始</v-btn>
      </v-card>

      <Q1Gender v-else-if="step === 1" v-model="gender" @next="nextStep" />
      <Q2Color v-else-if="step === 2" v-model="color" @next="nextStep" />
      <Q3Animal v-else-if="step === 3" v-model="animal" @next="nextStep" />
      <Q4Style v-else-if="step === 4" v-model="style" @next="nextStep" />

      <ResultView v-else 
      :gender="gender" 
      :color="color" 
      :animal="animal" 
      :style="style" 
      :diagnosis-data="diagnosisData" 
      @restart="restartDiagnosis" />
    </v-container>
  </v-app>
</template>

<script setup>
import { ref } from 'vue';
import Q1Gender from './components/Q1Gender.vue';
import Q2Color from './components/Q2Color.vue';
import Q3Animal from './components/Q3Animal.vue';
import Q4Style from './components/Q4Style.vue';
import ResultView from './components/ResultView.vue';
import diagnosisData from './assets/diagnosisData.json';

const step = ref(0);
const gender = ref('');
const color = ref('');
const animal = ref('');
const style = ref('');

const startDiagnosis = () => {
  step.value = 1;
};

const nextStep = () => {
  step.value++;
};

// 再診断処理
const restartDiagnosis = () => {
  step.value = 0;
  gender.value = '';
  color.value = '';
  animal.value = '';
  style.value = '';
};
</script>

