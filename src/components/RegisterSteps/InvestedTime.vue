<script setup lang="ts">
  import { ref } from 'vue';
  import CustomSelectable from '../CustomSelectable.vue'

  defineProps<{ 
    handleNext: () => void
  }>()

  const selectedItem = ref('0')
  const isDesktop = ref(window.screen.width >= 1024)
</script>

<template>
  <section class="time-step-wrapper">
    <div class="time-step-form">
      <p class="time-step-title">Por quanto tempo você pretende manter o patrimônio investido?</p>
      <div class="time-step-input-wrapper">
        <div class="time-step-input-container">
          <CustomSelectable @click="(value) => selectedItem = value" value="1" :is-selected="selectedItem === '1'">
            <span v-if="!isDesktop" class="time-step-selectable-text">Até <strong>1 ano</strong></span>
            <span v-else class="time-step-selectable-text">Até <strong>1</strong><strong>ano</strong></span>
          </CustomSelectable>
        </div>
        <div class="time-step-input-container">
          <CustomSelectable @click="(value) => selectedItem = value" value="2" :is-selected="selectedItem === '2'">
            <span v-if="!isDesktop" class="time-step-selectable-text">Entre <strong>1-5 anos</strong></span>
            <span v-else class="time-step-selectable-text">Entre <strong>1-5</strong><strong>anos</strong></span>
          </CustomSelectable>
        </div>
        <div class="time-step-input-container">
          <CustomSelectable @click="(value) => selectedItem = value" value="3" :is-selected="selectedItem === '3'">
            <span v-if="!isDesktop" class="time-step-selectable-text"><strong>5+ anos</strong></span>
            <span v-else class="time-step-selectable-text"><strong>5+</strong><strong>anos</strong></span>
          </CustomSelectable>
        </div>        
      </div>      
    </div>
    <div class="register-navigation-wrapper">
      <button :disabled="selectedItem === '0'" class="register-next-btn" @click="handleNext">Continuar</button>
    </div>
  </section>
</template>

<style lang="scss">
  .time-step {
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

    &-input-wrapper {
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
      }

    &-input-container {
      margin-top: 24px;
    }

    &-selectable-text {
      font-size: 16px;
      line-height: 25.6px;
      font-weight: 400;
      margin-left: 14px;

      strong {
        font-size: 36px;
        line-height: 57.6px;
        font-weight: 500;
        margin-left: 8px;
      }
    }
  }

  @media (min-width: 1024px) {
    .time-step {
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

      &-selectable-text {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 100%;
        font-size: 16px;
        line-height: 25.6px;
        font-weight: 400;
        margin: unset;
        margin-top: 30px;

        strong {
          font-size: 36px;
          line-height: 57.6px;
          font-weight: 500;
          margin: unset;
        }

        strong:first-child {
          font-size: 70px;
          line-height: 60px;
        }
      }
    }    
  }
</style>

