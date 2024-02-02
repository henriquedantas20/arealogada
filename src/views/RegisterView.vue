<script setup lang="ts">
    import { h, ref, shallowRef, defineComponent, type Component } from 'vue'
    import { 
      PersonalData, 
      RegisterData, 
      AddressInfo, 
      MarketExperience, 
      Objective, 
      InvestedTime, 
      KnownInvestments,
      InvestedAmount,
      MonthlyEarnings,
      Patrimony,
      Documents,
      RegisterSuccess
    } from '@/components/RegisterSteps'
    import CustomStepper from '@/components/CustomStepper.vue';
    import ChevronLeft from '@/assets/chevron-left.svg'

    const REGISTER_STEPS = {
      PersonalData,
      RegisterData,
      AddressInfo,
      MarketExperience,
      Objective,
      InvestedTime,
      KnownInvestments,
      InvestedAmount,
      MonthlyEarnings,
      Patrimony,
      Documents,
      RegisterSuccess
    }

    enum REGISTER_STEP_TYPES {
      PersonalData = 0,
      RegisterData,
      AddressInfo,
      MarketExperience,
      Objective,
      InvestedTime,
      KnownInvestments,
      InvestedAmount,
      MonthlyEarnings,
      Patrimony,
      Documents,
      RegisterSuccess
    }

    const handleSetComponent = (component: Component) => 
      defineComponent((props) => () => h(component, {...props, handleNext }))
    
    const currentStep = shallowRef(handleSetComponent(REGISTER_STEPS.PersonalData))
    const currentStepIndex = ref(0)

    const handleBack = () => {
      const previousStep = Object.values(REGISTER_STEPS).find((_, i) => i === currentStepIndex.value - 1)   

      if (previousStep) { 
        const previousComponent = handleSetComponent(previousStep)
        currentStep.value = previousComponent 
        currentStepIndex.value--
      }
    }

    const handleNext = () => {
      const nextStep = Object.values(REGISTER_STEPS).find((_, i) => i === currentStepIndex.value + 1)
      if (nextStep) { 
        const nextComponent = handleSetComponent(nextStep)
        currentStep.value = nextComponent 
        currentStepIndex.value++
      }
    }
</script>

<template>
  <main>
    <header class="register-header-wrapper">
      <img @click="handleBack" class="register-header-back-btn" :src="ChevronLeft" />
      <CustomStepper :current="currentStepIndex + 1" :total="REGISTER_STEP_TYPES.RegisterSuccess + 1" />
    </header>
    <section class="register-wrapper">
      <Transition mode="out-in">
        <component class="rendered-step-wrapper" v-bind="{ handleNext }" :is="currentStep"></component>
      </Transition>
    </section>
  </main>
</template>

<style lang="scss">
  main {
    height: 100%;
  }

  .register {
    &-header {
      &-wrapper {
        display: flex;
        align-items: center;
        width: 100%;
      }

      &-back-btn {
        width: 15px;
        height: 22px;
        margin-right: 20px;
      }
    }

    &-wrapper {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin-top: 26px;
        height: 95%;
    }
  }

  .register-navigation-wrapper {
    display: flex;
    justify-content: center;
    align-items: flex-end;
    height: 30%;
    padding-top: 20px;
  }

  .register-next-btn {
    width: 100%;
    height: 54px;
    border-radius: 20px;
    background-color: #FF4600;
    color: #fff;
    font-size: 18px;
    font-weight: 500;
    border: none;
    outline: none;
    font-family: 'IBM Plex Sans';

    &:disabled {
      background-color: #DDDDDD;
      color: #fff;
      cursor: not-allowed;
      font-weight: 500;
    }
  }

  .v-enter-active,
  .v-leave-active {
    transition: opacity 0.5s ease;
  }

  .v-enter-from,
  .v-leave-to {
    opacity: 0;
  }

  @media (min-width: 1024px) {
    main {
      width: 100%;
      height: 90%;
    }

    .register {
      &-header {
        &-wrapper {
          display: flex;
          align-items: center;
          width: 100%;
        }

        &-back-btn {
          width: 15px;
          height: 22px;
          margin-right: 20px;
          cursor: pointer;
        }
      }

      &-wrapper {
          display: flex;
          flex-direction: column;
          justify-content: space-between;
          height: 95%;
      }
    }

    .register-next-btn {
        width: 343px;
        height: 54px;
        border-radius: 20px;
        background-color: #FF4600;
        align-self: center;
        color: #fff;
        font-size: 18px;
        font-weight: 500;
        border: none;
        outline: none;
        cursor: pointer;
        transition: all .2s;
      
        &:hover {
          background-color: #ff946e;
          transition: all .2s;
        }

        &:disabled {
          background-color: #DDDDDD;
          color: black;
          cursor: not-allowed;
        }
      }      
  }
</style>
