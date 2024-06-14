<template>
  <q-btn v-bind="$props">
    <!-- QBtn has no scoped slots -->
    <template v-for="(_, slotName) in $slots" #[slotName]>
      <slot :name="slotName" />
    </template>
  </q-btn>
</template>

<script setup lang="ts">
import { QBtn, QBtnProps } from "quasar";
import { PropOptions } from "./types";
import dayjs from "dayjs";
import { onMounted } from "vue";

// You can also use <script setup lang="ts">, but it won't work in app-webpack JS apps
// without extra configuration in the app's webpack config
// If https://github.com/unjs/mkdist/pull/210 gets released, you will be able to use
// <script setup lang="ts"> if not using type-only macros, e.g. defineProps<QBtnProps>()
// If you will only use the app-extension by yourself or within your organization, and you
// don't have JS app-webpack apps, then you can freely use <script setup lang="ts">
defineProps({
  ...(QBtn["props"] as PropOptions<QBtnProps>),
  dense: {
    type: Boolean,
    default: true,
  },
  outline: {
    type: Boolean,
    default: true,
  },
});

onMounted(() => {
  console.log("instance mounted", dayjs);
});
</script>
