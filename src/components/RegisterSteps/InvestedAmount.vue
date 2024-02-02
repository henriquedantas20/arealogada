<script setup lang="ts">
  import CustomInput from '../CustomInput.vue'
</script>

<template>
  <section>
    <p>Teste</p>
    <div>
      <CustomInput label="Nome" name="name" value="" @change="(target) => console.log(target)" />
    </div>
  </section>
</template>
