<template>
  <Layout>
    <template #header>
      <Header> </Header>
    </template>
    <template #resume>
      <Resume />
    </template>
    <template #movements>
      <Movements />
    </template>
  </Layout>
</template>

<script setup>
import Layout from "./Layout.vue";
import Header from "./Header.vue";
import Resume from "./resume/Resume.vue";
import Movements from "./Movements.vue";
</script>
