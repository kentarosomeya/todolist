<template>
  <div>
    <div>ItemList</div>
    <div v-for="item in items" :key="item.name">
      <div class="item">
        <div class="name" :class="{ over500: count >= 1 }">タスク: {{ item.name }}
        <input type="checkbox">完了
        </div>
      </div>
    </div>
    <div>
      <label>
        名前
        <input v-model="newItemName" type="text" />
      </label>
      <button @click="addItem">add</button>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const count = ref(0);
    const items = ref([
    ]);
    const newItemName = ref("");
    const newItemPrice = ref(0);

    const addItem = () => {
      items.value.push({ name: newItemName.value, price: newItemPrice.value });
    };

    return { count, items, newItemName, newItemPrice, addItem };
  },
};
</script>

<style>
.over500 {
  color: red;
}
</style>