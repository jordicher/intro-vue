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
import { computed } from "vue";
import Layout from "./Layout.vue";
import Header from "./Header.vue";
import Resume from "./resume/Resume.vue";
import Movements from "./movements/Movements.vue";
import Action from "./Action.vue";
import Graphic from "./resume/Graphic.vue";

const amount = null;

const movements = [
  {
    id: 1,
    title: "Movimiento",
    description: "Deposito de salario",
    amount: "1000",
    time: new Date("10/05/2022"),
  },
  {
    id: 2,
    title: "Movimiento 1",
    description: "Deposito de honorarios",
    amount: "500",
    time: new Date("10/05/2022"),
  },
  {
    id: 3,
    title: "Movimiento 3",
    description: "Comida",
    amount: "100",
    time: new Date("10/05/2022"),
  },
  {
    id: 4,
    title: "Movimiento 4",
    description: "Colegiatura",
    amount: "500",
    time: new Date("13/05/2022"),
  },
  {
    id: 5,
    title: "Movimiento 5",
    description: "Reparación equipo",
    amount: "1000",
    time: new Date("15/05/2022"),
  },
];
const date = new Date().toDateString();

const amounts = computed(() => {
  const today = new Date();
  const oldDate = today.setDate(today.getDate() - 30);
  const lastDays = movements
    .filter((m) => m.time > oldDate)
    .map((m) => m.amount);

  return lastDays.map((m, i) => {
    const lastMovements = lastDays.slice(0, i);
    return lastMovements.reduce((suma, movement) => {
      return suma + movement;
    }, 0);
  });
});
</script>
