<template>
    <div v-if="visible" class="modal-overlay" @click.self="close">
      <div class="modal-content">
        <button class="close-button" @click="close">&times;</button>
        <slot></slot>
      </div>
    </div>
  </template>
  
  <script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  visible:{
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['close'])
const close = () => {
  emit('close');
} 
  </script>
  
  <style scoped>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .modal-content {
    background: white;
    padding: 20px;
    border-radius: 5px;
    position: relative;
    max-width: 300px;
    width: 100%;
  }
  
  .close-button {
    position: absolute;
    top: 10px;
    right: 10px;
    background: transparent;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
  }
  </style>
  