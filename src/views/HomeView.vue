<script setup>
import CountriesForm from '../components/countriesForm.vue'
import Toast from '../components/Toast.vue'
</script>

<template>
  <main class="mt-5">
    <CountriesForm />
    <Toast
    message="Le Pays est crée"
    class="text-bg-success"
    ></Toast>
  </main>
</template>
