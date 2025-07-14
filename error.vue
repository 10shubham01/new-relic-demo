<template>
  <div>
    {{ error.statusCode }}
  </div>
</template>
<script lang="ts" setup>
import type { NuxtError } from "#app";
const props = defineProps<{
  error: NuxtError;
}>();
console.log("hello");

useNuxtApp().$newRelic.api.addPageAction('log', {
  level: 'info',
  path: useRoute().fullPath,
  message: props.error.message
});
useNuxtApp().$newRelic.api.log('my log message', {customAttributes: {myFavoriteApp: true}})
</script>
