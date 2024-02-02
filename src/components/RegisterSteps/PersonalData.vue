<script setup lang="ts">
  import CustomInput from '../CustomInput.vue'
  import CustomSelect from '../CustomSelect.vue';

  defineProps<{ 
    handleNext: () => void
  }>()
</script>

<template>
  <section class="personal-step-wrapper">
    <div class="personal-step-form">
      <p class="personal-step-title">Dados Pessoais</p>
      <div class="personal-step-input-wrapper">
        <div class="personal-step-input-container">
          <CustomInput label="Nome" name="name" value="" @change="(target) => console.log(target)" />
        </div>
        <div class="personal-step-input-container">
          <CustomSelect
            :options="['Brasil', 'Estados Unidos']"
            label="Nacionalidade"
            :default="'Brasil'"
            class="select"
            @input="console.log($event)"
          />
        </div>
        <div class="personal-step-input-container">
          <CustomSelect
            :options="['Solteiro', 'Casado']"
            label="Estado Civil"
            class="select"
            @input="console.log($event)"
          />
        </div>
        <div class="personal-step-input-container">
          <CustomSelect
            :options="['Masculino', 'Feminino']"
            label="Sexo"
            class="select"
            @input="console.log($event)"
          />
        </div>
        <div class="personal-step-input-container">
          <CustomInput label="Profissão" name="name" value="" @change="(target) => console.log(target)" />
        </div>
      </div>
    </div>
    <div class="register-navigation-wrapper">
      <button class="register-next-btn" @click="handleNext">Continuar</button>
    </div>
  </section>
</template>

<style lang="scss">
  .personal-step {
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
  } 

  @media (min-width: 1024px) {
    .personal-step {
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
        overflow-y: auto;
      }

      &-input-container {
        width: 48%;
        height: 65px;
      }
    }    
  }
</style>
