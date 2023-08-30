

<template>
  <div>
    <button @click="toggleStatus">選考ステータス変更</button>
    
    <div v-if="showStatusSelector">
      <label for="status">選考ステータス:</label>
      <select id="status" v-model="interviewStatus">
        <option value="waiting">選考中</option>
        <option value="pass">合格</option>
        <option value="fail">不合格</option>
      </select>
    </div>

    <div v-if="interviewStatus === 'pass' && showStatusSelector">
      <label for="interviewer">次回面接担当者:</label>
      <select id="interviewer" v-model="selectedInterviewer">
        <option v-for="interviewer in interviewers" :key="interviewer.id" :value="interviewer.id">{{ interviewer.name }}</option>
      </select>
    </div>
    <button v-if="showStatusSelector">変更確定</button>
  
  </div>
</template>

<script setup>
import WelcomeItem from './WelcomeItem.vue'
import { ref } from 'vue';

const showStatusSelector = ref(false);
const interviewStatus = ref('pass'); // 初期値は合格
const selectedInterviewer = ref(''); // 面接担当者を選択するためのプロパティ

const interviewers = [
  { id: 'interviewer1', name: '担当者A' },
  { id: 'interviewer2', name: '担当者B' },
  { id: 'interviewer3', name: '担当者C' }
  // 必要なだけ面接担当者を追加
];

const toggleStatus = () => {
  showStatusSelector.value = !showStatusSelector.value;
};
</script>