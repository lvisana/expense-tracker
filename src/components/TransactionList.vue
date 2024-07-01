<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <template></template>
    <li
      v-for="trans in transactions"
      :key="trans.id"
      :class="trans.amount < 0 ? 'minus' : 'plus'"
    >
      {{ trans.text }} <span>${{ trans.amount }}</span
      ><button @click="deleteTransaction(trans.id)" class="delete-btn">
        x
      </button>
    </li>
  </ul>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["transactionDeleted"]);

const deleteTransaction = (id) => {
  emit("transactionDeleted", id);
};
</script>
