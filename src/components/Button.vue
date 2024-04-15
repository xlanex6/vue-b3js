<template>
  <button class="rounded-xl px-4 py-1 font-bold shadow-lg text-white mx-2" :class="styleMapper[variant]">
    <slot />
  </button>
</template>
<script setup>

const styleMapper = {
  success: 'bg-green-500 hover:bg-green-400',
  warning: 'bg-orange-500 hover:bg-orange-400',
  danger: 'bg-red-500 hover:bg-red-400'
}

defineProps({
  variant: {
    type: String,
    default: 'success',
    validator(value, props) {
      return ['success', 'warning', 'danger'].includes(value)
    }
  }
})

</script>


