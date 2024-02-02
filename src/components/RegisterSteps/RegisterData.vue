<script setup lang="ts">
  import CustomInput from '../CustomInput.vue'
  import CustomSelect from '../CustomSelect.vue';

  defineProps<{ 
    handleNext: () => void
  }>()
</script>

<template>
  <section class="register-step-wrapper">
    <div class="personal-step-form">
      <p class="register-step-title">Dados Cadastrais</p>
      <div class="register-step-input-wrapper">
        <div class="register-step-input-container">
          <CustomInput label="CPF" name="name" value="" @change="(target) => console.log(target)" />
        </div>
        <div class="register-step-input-container twin">
          <div class="register-step-half-input-container">
            <CustomInput label="RG" name="name" value="" @change="(target) => console.log(target)" />
          </div>
          <div class="register-step-half-input-container">
            <CustomSelect
              :options="['SSP']"
              label="Expedição"
              class="select"
              @input="console.log($event)"
            />
          </div>
        </div>
        <div class="register-step-input-container">
          <CustomInput label="E-mail" name="name" value="" @change="(target) => console.log(target)" />
        </div>
        <div class="register-step-input-container">
          <CustomInput label="Telefone" name="name" value="" @change="(target) => console.log(target)" />
        </div>
        <div class="register-step-input-container">
          <CustomInput label="Data de nascimento" name="name" value="" @change="(target) => console.log(target)" />
        </div>
      </div>
    </div>
    <div class="register-navigation-wrapper">
      <button class="register-next-btn" @click="handleNext">Continuar</button>
    </div>
  </section>
</template>

<style lang="scss">
 .register-step {
    &-wrapper {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      overflow-y: auto;
      padding-bottom: 20px;
      height: 100%;
    }

    &-title {
      font-size: 28px;
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
      width: 100%;
      margin-top: 24px;
    }

    &-input-container.twin {
      width: 100%;
      display: flex;
      justify-content: space-between;
    }

    &-half-input-container {
      width: 48%;
    }
  }   

  @media (min-width: 1024px) {
    .register-step {
      &-wrapper {
        display: flex;
        flex-direction: column;
        height: 100%;
        overflow-y: auto;
        padding-bottom: 20px;
      }

      &-title {
        width: auto;
        font-size: 28px;
        color: black;
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
      }

      &-input-container {
        width: 48%;
        height: 65px;
      }

      &-input-container.twin {
        width: 48%;
        display: flex;
        justify-content: space-between;
      }

      &-half-input-container:first-child {
        width: 65%;
      }

      &-half-input-container:last-child {
        width: 32%;
      }
    }    
  }
</style>
