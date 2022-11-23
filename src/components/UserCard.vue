<script setup>
import { toRef } from "vue";
const props = defineProps(["user"]);
const User = toRef(props, "user");
</script>
<template>
  {{ User }}
</template>
