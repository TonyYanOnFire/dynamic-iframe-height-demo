<script setup>
import {reactive} from 'vue'

const items = reactive(Array(10).fill(0).map(_ => {
  return {id: Math.random().toString(36).substr(2, 9)}
}))

const addItem = () => {
  items.push({id: Math.random().toString(36).substr(2, 9)})
}

const removeItem = (index) => {
  items.splice(index, 1)
}
</script>

<template>
  <div>
    <button @click="addItem">Add Item</button>
    <ul>
      <li v-for="(item, index) in items" :key="item.id" class="item">
        <button @click="removeItem(index)">Remove</button>
        <p style="font-size: 2em;">{{item.id}}</p>
      </li>
    </ul>
  </div>
</template>

<style>
.item {
    height: 100px;
    margin-bottom: 10px;
    width: 100%;
    height: 100px;
    background-color: #f7d1c2;
}
</style>