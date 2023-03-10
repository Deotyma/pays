<script setup>
const props = defineProps({
  message:{
    type:String,
    default:'Mon message'
  },
  class:{
    type:String,
    default:'text-bg-info'
  }
})
</script>

<template>
  <div class="toast-container position-fixed bottom-0 end-0 p-3">
    <div ref="toast1" id='showToast' class="toast" :class="class" role="alert">
      <div class="toast-body">
        <span>{{ message }}</span>
      </div>
    </div>
  </div>
</template>