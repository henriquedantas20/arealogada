<script setup lang="ts">
  import { ref } from 'vue';
  import CustomSelectable from '../CustomSelectable.vue'
  defineProps<{ 
    handleNext: () => void
  }>()

  const selectedItem = ref('0')
</script>

<template>
  <section class="market-step-wrapper">
    <div class="market-step-form">
      <p class="market-step-title">Qual sua formação acadêmica e experiência profissional voltadas para o mercado financeiro?</p>
      <div class="market-step-input-wrapper">
        <div class="market-step-input-container">
          <CustomSelectable @click="(value) => selectedItem = value" value="1" icon="🙇🏻" description="Não possuo formação acadêmica e/ou tenho pouco conhecimento sobre relação de risco-retorno de produtos complexos." :is-selected="selectedItem === '1'" />
        </div>
        <div class="market-step-input-container">
          <CustomSelectable @click="(value) => selectedItem = value" value="2" icon="🎓" description="Possuo formação acadêmica e/ou tenho algum conhecimento para entender relação de risco-retorno." :is-selected="selectedItem === '2'" />
        </div>
        <div class="market-step-input-container">
          <CustomSelectable @click="(value) => selectedItem = value" value="3" icon="📈" description="Possuo experiência no mercado financeiro e/ou tenho conhecimento de produtos complexos e entendo a relação de risco-retorno." :is-selected="selectedItem === '3'" />
        </div>
      </div>
    </div>
    <div class="register-navigation-wrapper">
      <button :disabled="selectedItem === '0'" class="register-next-btn" @click="handleNext">Continuar</button>
    </div>
  </section>
</template>

<style lang="scss">
  .market-step {
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
    .market-step {
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

