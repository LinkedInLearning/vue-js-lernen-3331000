<script setup>
import { ref } from 'vue'
const newItem = ref('')
const items = ref([
    { id: 1, title: 'Brot' },
    { id: 2, title: 'Tomaten' },
    { id: 3, title: 'Öl' },
])
const addItem = (() => {
    items.value.push({ id: items.value.length + 1, title: newItem.value })
    newItem.value = ''
})
</script>

<template>
    <h2>Composition API</h2>
    <!-- Beim Absenden des Formulars soll newItem
        der Liste hinzugefügt werden.
        Das Absenden des Formular soll unterbunden werden -->
    <form @submit.prevent="addItem">
        <label for="newItem">weiteren Artikel</label>
        <input id="newItem" v-model="newItem">
        <input type="submit">
    </form>
    <!-- Alle Inhalte der Einkaufliste in einer Schleife 
        ausgeben lassen-->
    <ol>
        <li v-for="item in items" :key="item.id">{{ item.title }}</li>
    </ol>
</template>
<style>
label {
    display: block;
}
</style>