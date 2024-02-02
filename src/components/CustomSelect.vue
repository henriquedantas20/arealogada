<template>
    <div class="custom-select" :tabindex="tabindex" @blur="open = false">
      <div class="selected" :class="{ open: open }" @click="open = !open">
        <p v-if="!!label" :class="[selected === null ? 'select-label active' : 'select-label']">{{ label }}</p>
        {{ selected }}
        <img :style="[open ? 'rotate: 90deg' : '']" class="select-arrow-down" :src="ChevronLeft" />
      </div>
      <div class="items" :class="{ selectHide: !open }">
        <div
          :key="-1"
          @click="
            selected = null;
            open = false;
            emits('input', null);
          "
        >
          {{ label }}
        </div>
        <div
          v-for="(option, i) of options"
          :key="i"
          @click="
            selected = option;
            open = false;
            emits('input', option);
          "
        >
          {{ option }}
        </div>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
    import { onMounted, ref } from 'vue';
    import ChevronLeft from '@/assets/chevron-left.svg'

    const props = defineProps<{
        options: Array<string>,
        default?: string,
        tabindex?: number,
        error?: string,
        label: string
    }>()

    const selected = ref(props.default ? props.default : null)
    const open = ref(false)

    const emits = defineEmits(["input"])
  </script>
  
  <style scoped>
  .custom-select {
    position: relative;
    width: 100%;
    text-align: left;
    outline: none;
    height: 65px;
    line-height: 47px;
  }

  .select-label {
    position: absolute;
    font-size: 12px;
    line-height: 13.2px;
    font-weight: 400;
    color: #515151;
    top: 12px;
    left: 22px;
    transition: all .2s;
  }

  .select-label.active {
    position: absolute;
    font-size: 16px;
    line-height: 17.6px;
    font-weight: 400;
    color: #515151;
    top: 25px;
    left: 22px;
    transition: all .2s;
  }
  
  .custom-select .selected {
    display: flex;
    align-items: center;
    background-color: #fff;
    border-radius: 20px;
    border: 1.5px solid #D5D5D5;
    height: 65px;
    color: #000;
    padding: 20px 20px 10px 20px;
    cursor: pointer;
    user-select: none;
    font-size: 16px;
    line-height: 17.6px;
    font-weight: 500;
  }
  
  .custom-select .selected.open {
    border-radius: 20px 20px 0px 0px;
  }
  
  .custom-select .selected:after {
    position: absolute;
    content: "";
    top: 22px;
    right: 1em;
    width: 0;
    height: 0;
    border: 5px solid transparent;
    border-color: #fff transparent transparent transparent;
  }
  
  .custom-select .items {
    color: #000;
    border-radius: 0px 0px 20px 20px;
    overflow: hidden;
    border-right: 1.5px solid #D5D5D5;
    border-left: 1.5px solid #D5D5D5;
    border-bottom: 1.5px solid #D5D5D5;
    position: absolute;
    background-color: #fff;
    left: 0;
    right: 0;
    z-index: 1;
  }
  
  .custom-select .items div {
    color: #000;
    padding-left: 1em;
    cursor: pointer;
    user-select: none;
  }
  
  .custom-select .items div:hover {
    background-color: #FF4600;
    color: #fff;
    transition: all .2s;
  }
  
  .selectHide {
    display: none;
  }

  .select-arrow-down {
    rotate: 270deg;
    position: absolute;
    right: 25px;
    transition: all .2s;
  }

  @media (min-width: 1024px) {
  
  }
  </style>
  