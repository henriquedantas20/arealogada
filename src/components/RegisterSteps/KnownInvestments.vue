<script setup lang="ts">
  import { ref } from 'vue';
  import CustomCarouselItem from '../CustomCarouselItem.vue'
  import ChartUpIcon from '../../assets/chart-up-icon.svg'

  defineProps<{ 
    handleNext: () => void
  }>()

  const selectedItem = ref('0')

  const carouselItemOptions = ["Sim, mas não investi recentemente", "Sim e investi nos últimos 12 meses", "Não"]

  type CarouselItemsType = {  
      icon: string
      title: string
      subtitle: string
      options:  Array<string>
  }[]

  const carouselOptions: CarouselItemsType = [
    {
      icon: ChartUpIcon,
      title: "Renda Fixa",
      subtitle: "Títulos públicos, CDBs, debêntures e outros títulos privados",
      options: carouselItemOptions
    },
    {
      icon: ChartUpIcon,
      title: "Fundo de Investimento",
      subtitle: "Fundos de renda fixa, fundos multimercados",
      options: carouselItemOptions
    },
    {
      icon: ChartUpIcon,
      title: "Renda Variável",
      subtitle: "Ações, fundos de ações, ETF",
      options: carouselItemOptions
    },
    {
      icon: ChartUpIcon,
      title: "Derivativos e COE",
      subtitle: "Opções, futuros, termos",
      options: carouselItemOptions
    },
    {
      icon: ChartUpIcon,
      title: "Criptoativos",
      subtitle: "Opções, futuros, termos",
      options: carouselItemOptions
    },
  ]
</script>

<template>
  <section class="known-step-wrapper">
    <div class="known-step-form">
      <p class="known-step-title">Você conhece ou já fez algum desses tipos de investimento?</p>
      <div class="known-step-input-wrapper">
        <div class="known-step-input-container" v-for="(option) of carouselOptions" :key="option.title">
          <CustomCarouselItem :icon="option.icon" :options="option.options" :title="option.title" :subtitle="option.subtitle" />
        </div>
      </div>
    </div>
    <div class="register-navigation-wrapper">
      <button :disabled="selectedItem === '0'" class="register-next-btn" @click="handleNext">Continuar</button>
    </div>
  </section>
</template>

<style lang="scss">
  .known-step {
    &-wrapper {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
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
        overflow-x: scroll;
        padding-bottom: 20px;

        &::-webkit-scrollbar {
          display: none;
        }
      }

    &-input-container {
      margin-top: 24px;
      margin-right: 24px;
      height: 436px;
    }
  }

  @media (min-width: 1024px) {
    .known-step {
      &-wrapper {
        display: flex;
        flex-direction: column;
        height: 100%;
        overflow-y: visible;
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
        justify-content: flex-start;
        align-content: start;
        overflow-y: auto;
      }

      &-input-container {
        width: 32%;
        height: 202px;
        margin-right: 10px;
      }
    }    
  }
</style>

