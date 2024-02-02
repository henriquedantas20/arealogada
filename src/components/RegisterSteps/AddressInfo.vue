<script setup lang="ts">
  import CustomInput from '../CustomInput.vue'
  import CustomSelect from '../CustomSelect.vue';

  defineProps<{ 
    handleNext: () => void
  }>()
</script>

<template>
  <section class="address-step-wrapper">
    <div class="address-step-form">
      <p class="address-step-title">Endereço</p>
      <div class="address-step-input-wrapper">
        <div class="address-step-input-container">
          <CustomInput label="CEP" name="name" value="" @change="(target) => console.log(target)" />
        </div>
        <div class="address-step-input-container twin">
          <div class="address-step-half-input-container">
            <CustomInput label="Cidade" name="name" value="" @change="(target) => console.log(target)" />
          </div>
          <div class="address-step-half-input-container">
            <CustomSelect
              :options="['SP']"
              label="UF"
              class="select"
              @input="console.log($event)"
            />
          </div>
        </div>
        <div class="address-step-input-container">
          <CustomInput label="Rua" name="name" value="" @change="(target) => console.log(target)" />
        </div>
        <div class="address-step-input-container twin inverted">
          <div class="address-step-half-input-container">
            <CustomInput label="Complemento" name="name" value="" @change="(target) => console.log(target)" />
          </div>
          <div class="address-step-half-input-container">
            <CustomInput label="Nº" name="name" value="" @change="(target) => console.log(target)" />
          </div>
        </div>
      </div>
    </div>
    <div class="register-navigation-wrapper">
      <button class="register-next-btn" @click="handleNext">Continuar</button>
    </div>
  </section>
</template>

<style lang="scss">
  .address-step {
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

    &-input-container.twin.inverted {
      flex-direction: row-reverse;
    }

    &-half-input-container:first-child {
      width: 65%;
    }

    &-half-input-container:last-child {
      width: 32%;
    }
  }   

  @media (min-width: 1024px) {
    .address-step {
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

