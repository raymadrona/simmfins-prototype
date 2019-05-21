<template>
  <q-layout>
    <q-page-container>
      <q-page class="q-ma-md">
        <q-btn type="a" href="/collection" icon="phone" label="Collection" stack glossy color="blue" />
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      dialog: true,
      maximizedToggle: false,
      tab: "loans"
    };
  }
};
</script>

<style></style>
