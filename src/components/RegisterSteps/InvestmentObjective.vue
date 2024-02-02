<script setup lang="ts">
  import { ref } from 'vue';
  import CustomSelectable from '../CustomSelectable.vue'
  defineProps<{ 
    handleNext: () => void
  }>()

  const selectedItem = ref('0')
</script>

<template>
  <section class="objective-step-wrapper">
    <div class="objective-step-form">
      <p class="objective-step-title">Qual o seu principal objetivo ao investir?</p>
      <div class="objective-step-input-wrapper">
        <div class="objective-step-input-container">
          <CustomSelectable @click="(value) => selectedItem = value" value="1" icon="🧘" description="Preservação de patrimônio" :is-selected="selectedItem === '1'" />
        </div>
        <div class="objective-step-input-container">
          <CustomSelectable @click="(value) => selectedItem = value" value="2" icon="🧐" description="Combinação entre preservação e valorização do patrimônio, assumindo um risco moderado" :is-selected="selectedItem === '2'" />
        </div>
        <div class="objective-step-input-container">
          <CustomSelectable @click="(value) => selectedItem = value" value="3" icon="🚀" description="Aumentar meus rendimentos, mesmo assumindo um risco maior" :is-selected="selectedItem === '3'" />
        </div>
      </div>
    </div>
    <div class="register-navigation-wrapper">
      <button :disabled="selectedItem === '0'" class="register-next-btn" @click="handleNext">Continuar</button>
    </div>
  </section>
</template>

<style lang="scss">
  .objective-step {
    &-wrapper {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      overflow-y: auto;
      padding-bottom: 20px;
      height: 100%;
    }

    &-title {
      font-size: 22px;
      line-height: 30.8px;
      color: black;
      font-weight: 500;
    }

    &-form {
      display: flex;
      flex-direction: column;
    }

    &-input-wrapper {
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
      }

    &-input-container {
      margin-top: 24px;
    }
  }

  @media (min-width: 1024px) {
    .objective-step {
      &-wrapper {
        display: flex;
        flex-direction: column;
        height: 100%;
        overflow-y: auto;
        padding-bottom: 20px;
      }

      &-title {
        width: 90%;
        font-size: 28px;
        color: black;
        line-height: 39.2px;
        font-weight: 500;
        margin-bottom: 93px;
      }

      &-form {
        display: flex;
        flex-direction: column;
        height: 100%;
      }

      &-input-wrapper {
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: space-between;
        align-content: start;
        overflow-y: auto;
      }

      &-input-container {
        width: 32%;
      }
    }    
  }
</style>

