<template>
  <Layout>
    <template #header>
      <Header> </Header>
    </template>
    <template #resume>
      <Resume
        :label="'Ahorro total'"
        :amount="amount"
        :total-amount="1000"
        :date="date"
      >
        <template #graphic>
          <Graphic :amounts="amounts" />
        </template>

        <template #action>
          <Action />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements" />
    </template>
  </Layout>
</template>

<script setup>
import Layout from "./Layout.vue";
import Header from "./Header.vue";
import Resume from "./resume/Resume.vue";
import Movements from "./movements/Movements.vue";
import Action from "./Action.vue";
import Graphic from "./resume/Graphic.vue";

const amount = null;
const amounts = [100, 200, 500, 200, -400, -600, -300, 0, 300, 500];
const date = new Date().toDateString();

const movements = [
  {
    id: 1,
    title: "Movimiento",
    description: "Deposito de salario",
    amount: "1000",
  },
  {
    id: 2,
    title: "Movimiento 1",
    description: "Deposito de honorarios",
    amount: "500",
  },
  {
    id: 3,
    title: "Movimiento 3",
    description: "Comida",
    amount: "-100",
  },
  {
    id: 4,
    title: "Movimiento 4",
    description: "Colegiatura",
    amount: "1000",
  },
  {
    id: 5,
    title: "Movimiento 5",
    description: "Reparación equipo",
    amount: "1000",
  },
];
</script>
